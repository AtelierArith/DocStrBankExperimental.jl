```
modeplot(ps_data, pkey [,z])
```

Pseudospectraオブジェクト`ps_data`にカプセル化された行列の固有モードまたは擬似固有モードを抽出してプロットします。提供された場合は値`z`を使用し、そうでなければプロンプトを表示します。`pkey`が1の場合は`z`の擬似固有モードを見つけ、それ以外の場合は`z`に最も近い固有値の固有モードを見つけます。
