```julia
struct GeneralizedLogistic
```

特定のパラメータ `a`、`b`、`c` を持つ一般化ロジスティック関数を表す型で、(線形) `EbN0` の関数として PLR 曲線を近似するために使用されます。近似関数は次の形式を取ります：

$$
f(E_bN_0) = (1 + exp(a ⋅ (E_bN_0 - b)))^{-c}
$$

この型の任意のインスタンスは、単一の数値 `ebno` を入力として呼び出すことができ、上記の式に従って得られた近似 PLR 値を返します。

# フィールド

  * `a::Float64`
  * `b::Float64`
  * `c::Float64`

# コンストラクタ

唯一のコンストラクタは、`a`、`b`、`c` パラメータをこの順序で表す3つの入力数値を受け取ります。

# 例

```jldoctest
julia> using TelecomUtils

julia> g = GeneralizedLogistic(3, 1.1, 1.2)
GeneralizedLogistic(3.0, 1.1, 1.2)

julia> g(1.3) # これは db の ebno ではなく、線形です
0.287945071618515
```

パッケージのルートフォルダにある `plr_fit_notebook.jl` ノートブックを参照して、実際のシミュレーションデータへのフィッティングの例を確認してください。
