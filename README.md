# Certbot + AppService 자동화 프로젝트
-` root domain에 대한 지원X` 에 대한 해결을 위함.
# 흐름
- 인증을 위한 Azure DNS 셋팅(txt, A record, CNAME)
- Certbot으로 SSL 인증서를 생성
- 인증서를 keyvault에 저장
- Azure DNS에서 A record 혹은 CNAME 복구

# 필요한 지식
- Cerbot에서 non-interaction 명령어
- SSL 인증시 필요한 것들 (txt record같은)
- Azure DNS 조작
- Azure Keyvault 조작

# 추후 설정할수도있는것
```buildoutcfg
You need to setup the right permissions for CDN to access your Key vault:
1) Register Azure CDN as an app in your Azure Active Directory (AAD) via PowerShell using this command:
 New-AzADServicePrincipal -ApplicationId "205478c0-bd83-4e1b-a9d6-db63a3e1e1c8".
2) Grant Azure CDN service the permission to access the secrets in your Key vault. Go to “Access policies” 
from your Key vault to add a new policy, then grant “Microsoft.Azure.Cdn” service principal a “get-secret” permission.
```
 
 
 ## 참고
 - With docker - https://certbot.eff.org/docs/install.html#running-with-docker
 - ACME client python - https://github.com/certbot/certbot/blob/master/acme/examples/http01_example.py
 - ACME client dns challenge - https://stackoverflow.com/questions/58506975/python-acme-v2-reuse-order-challenge
 
 