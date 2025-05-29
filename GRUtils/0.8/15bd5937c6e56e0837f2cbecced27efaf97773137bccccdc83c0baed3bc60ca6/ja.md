```
colormap(cmap)
colormap([cmap,] T::Type{<:Integer}[, byteorder::Bool=false])
```

現在のカラーマップの値を設定または取得します。

カラーマップを設定するために識別子 `cmap` を指定します。この識別子は、[GR 組み込みカラーマップ](https://gr-framework.org/colormaps.html) の名前を持つ数値または文字列であることができます。

現在のカラーマップで定義された色のセットを、16進数のカラーコードのベクトルとして返すために整数データ型 `T` を指定します。デフォルトでは、これらのコードはリトルエンディアンシステムの単語順RGB値を表します。オプションの引数 `byteorder` を `true` に設定すると、バイト順のコードとしてコードを取得できます。

引数 `cmap::Union{Integer, AbstractString}` または `T::Type{<:Integer}` のいずれかが必要です。`cmap` が指定されていない場合、前のカラーマップが現在のものとして残ります。`T` が指定されていない場合、関数は `nothing` を返します。

# 例

```julia
# 例のポイントデータを作成
x = 8 .* rand(100) .- 4
y = 8 .* rand(100) .- 4
z = sin.(x) + cos.(y)
# "hot" カラーマップを使用
colormap("hot")
contourf(x, y, z)

```
