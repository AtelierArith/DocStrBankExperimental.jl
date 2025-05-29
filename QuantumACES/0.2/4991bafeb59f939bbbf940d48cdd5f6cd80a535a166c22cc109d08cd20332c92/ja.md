```
CodeParameters
```

符号抽出回路のコードパラメータ。

これらは、データキュービットが最初に配置され、その後にアンシラキュービットが続くようにキュービットが配置されることを期待しており、これらのパラメータは[`check_code_parameters`](@ref)で確認する必要があります。

# フィールド

  * `qubits::Vector{Tuple{Int, Int}}`: コードキュービットの格子位置。
  * `qubit_layout::Matrix{String}`: コードキュービットのレイアウトの図。
  * `inverse_indices::Dict{Tuple{Int, Int}, Int}`: キュービット格子位置からそのインデックスへの逆マッピング。
  * `data_indices::Vector{Int}`: データキュービットのインデックス。
  * `ancilla_indices::Vector{Int}`: アンシラキュービットのインデックス。
  * `ancilla_x_indices::Vector{Int}`: アンシラXチェックキュービットのインデックス。
  * `ancilla_z_indices::Vector{Int}`: アンシラZチェックキュービットのインデックス。
  * `check_x_indices::Vector{Tuple{Vector{Int}, Vector{Int}}}`: 各Xチェックのための(アンシラ, データ)キュービットインデックスのペア。
  * `check_z_indices::Vector{Tuple{Vector{Int}, Vector{Int}}}`: 各Zチェックのための(アンシラ, データ)キュービットインデックスのペア。
  * `init_x_indices::Vector{Int}`: X基底で初期化するための論理X初期化キュービットインデックス。
  * `init_z_indices::Vector{Int}`: X基底で初期化するための論理Z初期化キュービットインデックス。
  * `logical_x_indices::Vector{Int}`: 論理X演算子キュービットインデックス。
  * `logical_z_indices::Vector{Int}`: 論理Z演算子キュービットインデックス。
