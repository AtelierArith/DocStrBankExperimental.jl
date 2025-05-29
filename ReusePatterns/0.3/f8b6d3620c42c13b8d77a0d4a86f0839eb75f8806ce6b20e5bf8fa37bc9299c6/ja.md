`forward(sender::Tuple{Type,Symbol}, receiver::Type, method::Method; withtypes=true, allargs=true)`

`method` 呼び出しを `sender` 型から受信者型に適切に転送する `Vector{String}` を返します。

`sender` タプルは構造体型と、そのフィールドの名前を持つシンボルを含む必要があります。

`withtypes` キーワードは、転送メソッドが型注釈付きの引数を持つかどうかを制御します。 `allargs` キーワードは、すべての引数を使用するか、`receiver` 型を含む最後の引数までの最初の引数のみを使用するかを制御します。

両方のキーワードはデフォルトで `true` ですが、転送されるメソッドの数を減らすために `false` に設定することができます。

# 例:

`Int` オブジェクトのラッパーを実装し、`Int` を受け入れる `+` メソッドを転送します:

```julia-repl
struct Wrapper{T}
    wrappee::T
    extra
    Wrapper{T}(args...; kw...) where T = new(T(args...; kw...), nothing)
end

# 転送メソッドを準備して評価します:
m = forward((Wrapper, :wrappee), Int, which(+, (Int, Int)))
eval.(Meta.parse.(m))

# 2つのラップされた `Int` をインスタンス化します
i1 = Wrapper{Int}(1)
i2 = Wrapper{Int}(2)

# そしてシームレスに加算します
println(i1 +  2)
println( 1 + i2)
println(i1 + i2)
```
