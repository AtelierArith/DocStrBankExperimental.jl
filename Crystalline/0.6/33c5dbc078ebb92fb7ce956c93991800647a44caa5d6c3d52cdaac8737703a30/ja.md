```
classcharacters(irs::AbstractVector{<:AbstractIrrep}, αβγ=nothing)
```

`AbstractIrrep`s `irs` の共役類に関連するキャラクターテーブルを計算し、`ClassCharacterTable` を返します。

キャラクターは共役類のみに依存するため（これはレイまたは射影的な表現には当てはまりません）、クラス固有のキャラクターは、各操作のキャラクター（[`characters`](@ref) によって返される）と同じ情報をより簡潔に伝えることがよくあります。

参照: [`classes`](@ref).

## オプション引数

オプションとして、具体的な自由パラメータで irrep（および関連するキャラクター）を評価するために `αβγ::AbstractVector{<:Real}` 変数を渡すことができます（例: `LGIrrep`s の場合、"line-irrep" からサンプリングされた具体的な **k**-ベクトル）。デフォルトは `nothing` で、これは無関係であることを示します（例: `PGIrrep`s の場合）またはすべての自由パラメータが暗黙的にゼロに設定されていることを示します。
