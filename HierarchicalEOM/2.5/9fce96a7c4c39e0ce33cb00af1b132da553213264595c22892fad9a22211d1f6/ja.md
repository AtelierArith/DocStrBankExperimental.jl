```
struct Nvec
```

各多重インデックスアンサンブルの繰り返し数を補助密度演算子で記述するオブジェクトです。

`n_vector` ($\vec{n}$) は整数の集合を示します：

$$
\{ n_{1,1}, ..., n_{\alpha, k}, ... \}
$$

これは、$\alpha$-th バスにおける $k$-th 指数展開項に関連しています。もし $n_{\alpha, k} = 3$ であれば、これは多重インデックスアンサンブル $\{\alpha, k\}$ が ADO の多重インデックスベクトルに三回現れることを意味します（私たちの論文の表記を参照してください）。

`n_vector` の階層レベル ($L$) は $L=\sum_{\alpha, k} n_{\alpha, k}$ で与えられます。

# フィールド

  * `data` : `n_vector`
  * `level` : `n_vector` のレベル `L`

# メソッド

特定のインデックス (`idx`) に対する繰り返し数は、`n_vector[idx]` を呼び出すことで取得できます。与えられたインデックス `idx` に対する対応するタプル $(\alpha, k)$ を取得するには、詳細については [`HierarchyDict`](@ref) の `bathPtr` を参照してください。

`HierarchicalEOM.jl` は以下の呼び出し（メソッド）もサポートしています：

```julia
length(n_vector);  # `Nvec` の長さを返します
n_vector[1:idx];   # インデックス `1` から `idx` までの `n_vector` の励起数を含むベクトルを返します
n_vector[1:end];   # `n_vector` のすべての励起数を含むベクトルを返します
n_vector[:];       # `n_vector` のすべての励起数を含むベクトルを返します
from n in n_vector  # 繰り返し
    # 何かをする
end
```
