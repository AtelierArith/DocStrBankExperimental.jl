`SharedTBModel`は、すべての`TBModel`の情報をいくつかのSharedArraysにエンコードするデータ型です。

`SharedTBModel`は一般的に`TBModel`よりも効率的です。典型的なワークフローは、`TBModel`を構築し、その後大規模計算のために`SharedTBModel`に変換することです。

# フィールド

  * `norbits::Int64`: 軌道の数
  * `isorthogonal::Bool`: モデルの軌道が直交正規であるかどうか
  * `lat::SMatrix{3,3,Float64,9}`: 列に格納された原始格子ベクトル
  * `rlat::SMatrix{3,3,Float64,9}`: 列に格納された原始逆格子ベクトル
  * `Rs::Matrix{Int16}`: ホッピング、重なり、位置行列のために列に格納されたRベクトル。Rベクトルの数は奇数です。最初のRベクトルは[0, 0, 0]です。残りの行列`Rs[:, 2:end]`について、前半と後半は一対一対応のR <-> -Rであることが保証されています。
  * `Rcs::Matrix{Float64}`: デカルト座標系のRベクトル。
  * `H::SharedArray{T,2}`: `H = reshape(Hmatrix, (norbits * norbits, :))`。`Hmatrix[:, :, iR]`は⟨0n|H|Rm⟩であり、Rは`Rs[:, iR]`です。ハミルトニアンはエルミートであるため、`Rs`の最初の半分のRベクトルのみが格納されます。さらに、`Hmatrix[:, :, 1]`は異なります：`Hmatrix[:, :, 1]`は⟨0n|H|0m⟩/2です。
  * `S::Union{Nothing,SharedArray{T,3}}`: `S = reshape(Smatrix, (norbits * norbits, :))`。`Smatrix[:, :, iR]`は⟨0n|Rm⟩であり、Rは`Rs[:, iR]`です。重なり行列はエルミートであるため、`Rs`の最初の半分のRベクトルのみが格納されます。さらに、`Smatrix[:, :, 1]`は異なります：`Smatrix[:, :, 1]`は⟨0n|0m⟩/2です。
  * `r:SVector{3,SharedArray{T,2}}`: `S[α] = reshape(Smatrices[α], (norbits * norbits, :))`。`Smatrices[α][:, :, iR]`は⟨0n|rα|Rm⟩であり、Rは`Rs[:, iR]`です。
