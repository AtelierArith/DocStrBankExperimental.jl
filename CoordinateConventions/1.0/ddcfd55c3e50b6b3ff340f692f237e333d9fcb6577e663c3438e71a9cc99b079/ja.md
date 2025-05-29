```
check_cocos(B0, Ip, F::AbstractVector, pprime::AbstractVector, q::AbstractVector, psi::AbstracVector, cc::COCOS; verbose = false) -> Bool
```

与えられたCOCOSと一致する平衡量を返します

引数:

  * B0 - トロイダル磁場
  * Ip - プラズマ電流
  * F::AbstractVector - psiの関数としてのポロイダル電流
  * pprime::AbstracVector - psiの関数としてのpsiに対する圧力勾配
  * psi::AbstractVector - ポロイダルフラックス
  * cc::Union{Int,COCOS} - COCOS構造またはID
