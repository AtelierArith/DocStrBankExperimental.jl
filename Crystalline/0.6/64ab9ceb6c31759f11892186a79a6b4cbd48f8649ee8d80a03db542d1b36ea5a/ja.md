```
characters(irs::AbstractVector{<:AbstractIrrep}, αβγ=nothing)
```

`AbstractIrrep`のベクトル`irs`に関連するキャラクターテーブルを計算し、`CharacterTable`を返します。

## オプション引数

オプションとして、具体的な自由パラメータでirrep（および関連するキャラクター）を評価するために、`αβγ::AbstractVector{<:Real}`変数を渡すことができます（例：`LGIrrep`の場合、"line-irrep"からサンプリングされた具体的な**k**-ベクトル）。デフォルトは`nothing`で、これは無関係であることを示します（例：`PGIrrep`の場合）またはすべての自由パラメータが暗黙的にゼロに設定されていることを示します。
