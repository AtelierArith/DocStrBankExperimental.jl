```
SkipConnection(layer, connection)
```

レイヤーまたは連続するレイヤーの `Chain` からなるスキップ接続を作成し、ブロックの入力をユーザーが提供した2引数の呼び出し可能オブジェクトを介して出力にリンクするショートカット接続を作成します。呼び出し可能オブジェクトへの最初の引数は、指定された `layer` を通じて伝播され、2番目は変更されていない「スキップされた」入力です。

最も単純な「ResNet」タイプの接続は、単に `SkipConnection(layer, +)` です。以下は、より複雑な例です：

```jldoctest
julia> m = Conv((3,3), 4 => 7, pad=(1,1));

julia> x = ones(Float32, 5, 5, 4, 10);

julia> size(m(x)) == (5, 5, 7, 10)
true

julia> sm = SkipConnection(m, (mx, x) -> cat(mx, x, dims=3));

julia> size(sm(x)) == (5, 5, 11, 10)
true
```

他にも [`Parallel`](@ref)、[`Maxout`](@ref) を参照してください。
