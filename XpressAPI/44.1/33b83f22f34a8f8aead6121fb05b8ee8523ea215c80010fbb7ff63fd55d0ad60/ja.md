```
XPRS_LPSTATUS
```

LPソリューションのステータス。（整数）

値：0 : 未開始（`XPRS_LP_UNSTARTED`）。1 : 最適（`XPRS_LP_OPTIMAL`）。2 : 不可解（`XPRS_LP_INFEAS`）。3 : カットオフよりも目的が悪い（`XPRS_LP_CUTOFF`）。4 : 未完了（`XPRS_LP_UNFINISHED`）。5 : 無限大（`XPRS_LP_UNBOUNDED`）。6 : 双対でのカットオフ（`XPRS_LP_CUTOFF_IN_DUAL`）。7 : 数値的な問題により問題を解決できませんでした。（`XPRS_LP_UNSOLVED`）。8 : 問題には凸でない二次データが含まれています（`XPRS_LP_NONCONVEX`）。FICO Xpress Globalの使用を検討してください。
