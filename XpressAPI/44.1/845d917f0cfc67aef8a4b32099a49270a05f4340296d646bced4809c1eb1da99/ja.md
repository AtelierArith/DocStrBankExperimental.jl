```
XPRS_MIPSTATUS
```

(MIP) ソリューションステータス。(整数)

値: 0 : 問題が読み込まれていない (`XPRS_MIP_NOT_LOADED`). 1 : MIP 検索が不完全 - 初期の連続緩和が解決されておらず、整数解が見つかっていない (`XPRS_MIP_LP_NOT_OPTIMAL`). 2 : MIP 検索が不完全 - 初期の連続緩和が解決されており、整数解が見つかっていない (`XPRS_MIP_LP_OPTIMAL`). 3 : MIP 検索が不完全 - 整数解が見つかっていない (`XPRS_MIP_NO_SOL_FOUND`). 4 : MIP 検索が不完全 - 整数解が見つかっている (`XPRS_MIP_SOLUTION`). 5 : MIP 検索が完了 - 整数解が見つかっていない (`XPRS_MIP_INFEAS`). 6 : MIP 検索が完了 - 整数解が見つかっている (`XPRS_MIP_OPTIMAL`). 7 : MIP 検索が不完全 - 初期の連続緩和が無限大であることが判明した。解が見つかっている可能性がある (`XPRS_MIP_UNBOUNDED`).
