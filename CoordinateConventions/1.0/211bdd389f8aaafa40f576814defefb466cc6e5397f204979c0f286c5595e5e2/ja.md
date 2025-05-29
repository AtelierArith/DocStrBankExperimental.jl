```
check_cocos(sigma_B0, sigma_Ip, sigma_F, sigma_pprime, sigma_q, sigma_dpsi, cc::COCOS; verbose = false) -> Bool
```

与えられたCOCOSと一致する平衡量を返します

引数:

  * sigma_B0 - トロイダル磁場の符号
  * sigma_Ip - プラズマ電流の符号
  * sigma_F - ポロイダル電流の符号
  * sigma_pprime - 圧力勾配の符号
  * sigma_dpsi - dpsi/drの符号
  * cc::Union{Int,COCOS} - COCOS構造またはID
