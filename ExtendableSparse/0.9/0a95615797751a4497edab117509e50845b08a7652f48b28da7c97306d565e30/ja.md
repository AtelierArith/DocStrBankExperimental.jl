```julia
mutable struct SparseMatrixLNK{Tv, Ti<:Integer} <: SparseArrays.AbstractSparseArray{Tv, Ti<:Integer, 2}
```

リンクリスト形式のスパース行列を保持する構造体です。

Y. Saadによって記述された[ホワイトペーパー](https://www-users.cs.umn.edu/~saad/software/SPARSKIT/paper.ps)および[SPARSEKIT2ソースコード](https://www-users.cs.umn.edu/~saad/software/SPARSKIT/SPARSKIT2.tar.gz)に基づいてモデル化されています。彼は「これはスパース行列計算に使用される最も古いデータ構造の1つです。」と書いています。

関連するソースは[formats.f](https://salsa.debian.org/science-team/sparskit/blob/master/FORMATS/formats.f)もdebian/science gitlabで入手可能です。

リンクリスト構造の利点は、新しいエントリを挿入する際に、構造を説明する配列がそれぞれの端で成長し、`push!`を介して便利に更新できることです。既存のデータをコピーする必要はありません。

  * `m::Integer`: 行数
  * `n::Integer`: 列数
  * `nnz::Integer`: 非ゼロ数
  * `nentries::Integer`: 配列の長さ
  * `colptr::Vector{Ti} where Ti<:Integer`: 列エントリのリンクリスト。初期長さはnで、新しいエントリごとに成長します。

    colptr[index]はリスト内の次のインデックスを含むか、ゼロを含み、後者の場合は列jごとにインデックス1<=j<=nで始まるリストを終了します。
  * `rowval::Vector{Ti} where Ti<:Integer`: 行番号。各インデックスにはゼロ（初期状態）またはcolptr内の列エントリリストに対応する行番号が含まれます。

    初期長さはnで、新しいエントリごとに成長します。
  * `nzval::Vector`: 各ペア（colptr[index], rowval[index]）に対応する非ゼロエントリ値

    初期長さはnで、新しいエントリごとに成長します。
