```
struct ErrorModel
```

この構造体は、特定のエラーモデルに対してコヒーレントノイズ、非コヒーレントノイズ、および読み出しエラーをシミュレートするために使用されるすべての情報を保持します。構造は次のとおりです。

# 引数

  * `confusion_mat`: 量子ビットの数に応じて混同行列を生成する関数で、

型は`(Int)->(T)`、ここで`T`は行列のようなものです。

  * `collapse_ops`: 量子ビットの数に応じて崩壊演算子を生成する関数で、型は

`(Int)->Vector{SparseMatrixCSC}`です。

  * `coherent_noise`: ハミルトニアンからランダムサンプルを生成する関数を返す関数で、

型は`(RydbergHamiltonian)->(()->RydbergHamiltonian)`です。
