```
rydberg_density_sum([f], reg_or_samples)
```

ライデバーグ密度の合計。

# 引数

  * `f`: オプションの後処理コールバック関数 `f(config) -> config`。入力 `config` は `Int` 型の整数で、出力 `config` は [`count_vertices`](@ref) をサポートする型、例えば `AbstractVector` または `Integer` です。
  * `reg_or_samples` はレジスタ (`Yao.ArrayReg` または [`SubspaceArrayReg`](@ref)) であるか、`AbstractVector` における測定結果 (config) のリストです。

# 例

MIS実験における後処理プロトコルを実装するには：

1. まず構成を独立集合に減少させて `rydberg_density_sum` を計算します。

[`to_independent_set`](@ref) を使用します。

2. 頂点をランダムに追加し、次に最大の [`count_vertices`](@ref) を選択します。

[`add_random_vertices`](@ref) を使用します。

```julia
rydberg_density_sum(r) do config
    config = to_independent_set(config, graph)
    add_random_vertices(config, graph, 10)
    return config
end
```

または、原子の順序で頂点を追加することもできます。

```julia
rydberg_density_sum(r) do config
    config = to_independent_set(config, graph)
    add_vertices!(config, graph)
    return config
end
```
