```
P = hinfpartition(G, WS, WU, WT)
```

SISOまたはMIMOシステム$G$を、重み関数$W_S, W_U, W_T$を用いて孤立したコントローラを持つLFTに変換し、結果として得られるシステム$P(s)$を状態空間形式で記述します。$G$の有効な入力は、伝達関数（ダイナミクスを持ち、MIMOおよびSISOの両方、tfおよびss形式の両方）です。重み関数の有効な入力は、空の配列、数値（静的ゲイン）、および`LTISystem`です。

注意、`system_mapping(P)`は`-G`に等しいです。

# 拡張ヘルプ

条件が悪いMIMOプラントの場合、$S, CS, T$の重み付けは、プラントを「反転」させるコントローラをもたらす可能性があり、これによりロバスト性が低下することがあります。そのようなシステムでは、$GS$と$T$にペナルティを課す方が適切かもしれません。参考文献: "Inverting and noninverting H∞ controllers", Urs Christen, Hans Geering
