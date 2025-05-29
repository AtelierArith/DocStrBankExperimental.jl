```
struct DefaultIndexHandler{N} <: AbstractIndexHandler
    offset::Int
    perm::NTuple{N,Int}
end
```

`s`種の種を持つシステムの状態を`s`次元配列に格納する基本的なインデックスハンドラーです。`offset`パラメータは、配列がインデックスされるオフセットを示します（デフォルトはJuliaで1です）。種の順序はタプル`perm`によって与えられます。

これは最も単純なインデックスハンドラーですが、初期状態から到達できない状態がある場合（例えば、保存法則の存在による）、最適ではありません。このような場合は、可能な限り冗長な種を削除するようにしてください。

コンストラクタ: `DefaultIndexHandler([sys::FSPSystem, offset::Int=1])`
