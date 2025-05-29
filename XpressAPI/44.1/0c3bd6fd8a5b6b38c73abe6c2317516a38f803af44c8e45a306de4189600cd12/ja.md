```
XPRS_OPTIMIZETYPEUSED
```

最後のXPRSoptimize、XPRSmipoptimize、XPRSlpoptimize、または`XPRSnlpoptimize`の呼び出しで使用されたソルバーのタイプ。(整数)

値: -1 : ソルバーはまだ選択されていません(`XPRS_OPTIMIZETYPE_NONE`)。これは、問題のタイプを決定している間に解決が中断された場合に発生する可能性があります。 0 : LPソルバーが選択されました(`XPRS_OPTIMIZETYPE_LP`)。デフォルトで使用されるLPアルゴリズムはDEFAULTALGによって制御されます。 1 : MIPソルバーが選択されました(`XPRS_OPTIMIZETYPE_MIP`)。 2 : ローカル非線形ソルバーが選択されました(`XPRS_OPTIMIZETYPE_LOCAL`)。どのローカルソルバーが選択されたかはXPRS*LOCALSOLVERSELECTEDを参照してください。 3 : グローバル非線形ソルバーが選択されました(`XPRS*OPTIMIZETYPE_GLOBAL`)。
