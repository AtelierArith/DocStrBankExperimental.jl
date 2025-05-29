```
SparseMatrix{T}
```

型 `T` のスパース行列のための複合データ型です。

この構造体には以下のフィールドがあります：

  * `const nrow::Int`: 行数
  * `const ncol::Int`: 列数
  * `const char::Int`: 型 `T` の特性
  * `const zero::T`: 型 `T` の数 0
  * `const one::T`: 型 `T` の数 1
  * `entries::Vector{Vector{T}}`: `columns` に対応する行列のエントリ
  * `columns::Vector{Vector{Int}}`: `column[k]` は列 k の非ゼロエントリを指します
  * `rows::Vector{Vector{Int}}`: `rows[k]` は k 行目の非ゼロエントリを指します
