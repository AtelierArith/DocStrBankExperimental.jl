```
LatticeConnectivity <:AbstractConnectivity
```

任意系のQPUの二次元格子キュービット接続性を記述するデータ構造。この接続タイプは、[`AnyonYamaskaQPU`](@ref)のような`QPUs`で遭遇します。

# フィールド

  * `qubits_per_printout_line::Vector{Int}` – プリントアウトを構築する際の各行のキュービット数。
  * `dimensions              ::Vector{Int}` – 行と列の数（プリントアウトで45°回転）。
  * `excluded_positions      ::Vector{Int}` – オプション: 操作を実行できない無効な接続のキュービットのリスト。`Vector`の要素は一意でなければなりません。
  * `excluded_connections::Vector{Tuple{Int, Int}}` – オプション: 2キュービットゲートを実行できない無効なキュービット間の接続のリスト。`Vector`の要素は一意でなければなりません。各接続はキュービットインデックスの`Tuple`として提供されます。

# 例

次の格子は3行あり、各行には4つの要素があります。行にはキュービット `[1, 2, 3, 4]`、`[ 5, 6, 7, 8]`、および `[9, 10, 11, 12]` が含まれています。

対応する `qubits_per_printout_line` フィールドは `[1, 3, 3, 3, 2]` です。これは、印刷された表現の各行のキュービット数を含んでいます。

```jldoctest
julia> connectivity = LatticeConnectivity(3, 4)
LatticeConnectivity{3,4}
        1 
        | 
  9 ──  5 ──  2 
        |     | 
       10 ──  6 ──  3 
              |     | 
             11 ──  7 ──  4 
                    |     | 
                   12 ──  8 


```

任意の次元の格子を構築できます：

```jldoctest
julia> connectivity = LatticeConnectivity(6, 4)
LatticeConnectivity{6,4}
              1 
              | 
        9 ──  5 ──  2 
        |     |     | 
 17 ── 13 ── 10 ──  6 ──  3 
  |     |     |     |     | 
 21 ── 18 ── 14 ── 11 ──  7 ──  4 
        |     |     |     |     | 
       22 ── 19 ── 15 ── 12 ──  8 
              |     |     | 
             23 ── 20 ── 16 
                    | 
                   24 
```

オプションで、除外された位置を持つ格子を定義できます：

```jldoctest
julia> connectivity = LatticeConnectivity(3, 4, [1, 5, 9])
LatticeConnectivity{3,4}
        1 
        | 
  9 ──  5 ──  2 
        |     | 
       10 ──  6 ──  3 
              |     | 
             11 ──  7 ──  4 
                    |     | 
                   12 ──  8 

除外された位置: [1, 5, 9]
```
