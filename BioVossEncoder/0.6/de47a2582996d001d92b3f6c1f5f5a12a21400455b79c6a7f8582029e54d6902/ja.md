```
struct VossEncoder{A<:NucleicAcidAlphabet, B<:BitMatrix}
```

`VossEncoder`構造体は、核酸の配列をエンコードするバイナリ行列を表します。これは、配列のVoss表現とも呼ばれます。

# フィールド

  * `alphabet::A`: エンコードに使用される核酸アルファベット。
  * `bitmatrix::B`: エンコードされた配列を表すバイナリ行列。

# コンストラクタ

  * `VossEncoder(sequence::SeqOrView{A})`: 核酸の配列から`VossEncoder`を構築します。

## 引数

  * `sequence::SeqOrView{A}`: エンコードされる核酸の配列。
