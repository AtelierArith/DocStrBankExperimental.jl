```
XPRS_NODESELECTION
```

分岐と境界: これは、現在のノードが解決された後に解決のために考慮されるノードを決定します。(整数)

デフォルト値: 行列の特性に依存します。

値: 1 : ローカルファースト: 利用可能な場合は子孫ノードと兄弟ノードの間から選択; そうでなければすべての未解決ノードから選択。 2 : ベストファースト: すべての未解決ノードから選択。 3 : ローカル深さ優先: 利用可能な場合は子孫ノードと兄弟ノードの間から選択; そうでなければ最も深いノードから選択。 4 : ベストファースト、その後ローカルファースト: 最初のBREADTHFIRSTノードにはベストファーストが使用され、その後ローカルファーストが使用されます。 5 : 純粋な深さ優先: 最も深い未解決ノードから選択。
