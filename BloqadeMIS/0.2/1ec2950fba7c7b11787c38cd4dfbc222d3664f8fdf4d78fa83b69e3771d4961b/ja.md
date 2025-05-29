```
gibbs_loss([f], reg_or_samples, α::Real)
```

最大独立集合のためのギブス損失は次のように定義されます。

$$
L = -1/α \log(\langle ψ|\exp(α \sum(n))|ψ\rangle),
$$

ここで `n` は頂点集合のサイズです。

# 引数

  * `f`: オプションの後処理コールバック関数 `f(config) -> config`。入力 `config` は `Int` 型の整数で、出力 `config` は [`count_vertices`](@ref) をサポートする型、例えば `AbstractVector` または `Integer` です。
  * `reg_or_samples` はレジスタ (`Yao.ArrayReg` または [`SubspaceArrayReg`](@ref)) であるか、`AbstractVector` 内の測定結果 (config) のリストです。
  * `α::Real`: ギブス損失のパラメータです。
