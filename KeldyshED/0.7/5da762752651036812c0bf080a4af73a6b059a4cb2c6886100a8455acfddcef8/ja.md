有限系のフェルミオンのための軽量正確対角化ソルバー。

## フィールド

  * `full_hs::KeldyshED.Hilbert.FullHilbertSpace`: 系の全ヒルベルト空間。
  * `subspaces::Vector{KeldyshED.Hilbert.HilbertSubspace}`: ハミルトニアンの不変部分空間のリスト。
  * `eigensystems::Vector{KeldyshED.EigenSystem}`: 不変部分空間内のハミルトニアンの固有系。
  * `creation_connection::Vector{Dict{Int64, Int64}}`: 創成演算子 $c^\dagger_i$ によって生成された部分空間間の接続。もし、複合インデックス $i$ が `full_hs.soi` によって線形インデックス `l` に変換される創成演算子が部分空間 $s$ と $s'$ の間で作用する場合、`creation_connection[l][s] = s'` となる。
  * `annihilation_connection::Vector{Dict{Int64, Int64}}`: 消滅演算子 $c_i$ によって生成された部分空間間の接続。もし、複合インデックス $i$ が `full_hs.soi` によって線形インデックス `l` に変換される消滅演算子が部分空間 $s$ と $s'$ の間で作用する場合、`annihilation_connection[l][s] = s'` となる。
  * `cdag_matrices::Array{Dict{Int64, Matrix{ScalarType}}, 1} where ScalarType<:Number`: ハミルトニアンの固有基底における創成演算子 $c^\dagger_i$ の行列。もし、複合インデックス $i$ が `full_hs.soi` によって線形インデックス `l` に変換される創成演算子が部分空間 $s$ と $s'$ の間で作用する場合、その行列形式の対応するブロックは `cdag_matrices[l][s]` として利用可能である。
  * `c_matrices::Array{Dict{Int64, Matrix{ScalarType}}, 1} where ScalarType<:Number`: ハミルトニアンの固有基底における消滅演算子 $c_i$ の行列。もし、複合インデックス $i$ が `full_hs.soi` によって線形インデックス `l` に変換される消滅演算子が部分空間 $s$ と $s'$ の間で作用する場合、その行列形式の対応するブロックは `c_matrices[l][s]` として利用可能である。
  * `gs_energy::Float64`: 系の基底状態エネルギー。
