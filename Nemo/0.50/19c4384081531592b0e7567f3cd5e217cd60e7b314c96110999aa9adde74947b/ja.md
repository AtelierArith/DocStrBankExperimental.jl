```
mul_red!(z::AbsSimpleNumFieldElem, x::AbsSimpleNumFieldElem, y::AbsSimpleNumFieldElem, red::Bool)
```

$$
x
$$

と$y$を掛け算し、既存の数体要素$z$を結果に設定します。定義多項式による剰余は、`red`が`true`に設定されている場合のみ実行されます。$x$と$y$は減算されている必要があります。この関数は、新しいオブジェクトを結果のために割り当てることを避け、関連するガーベジコレクションを排除するため、パフォーマンスの理由で提供されています。
