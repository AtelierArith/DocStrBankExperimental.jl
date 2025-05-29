```julia
load_alist(
    file_path;
    check_redundant,
    warn_unexpected_file_extension
)

```

テキストファイルからLDPC行列をalist形式で読み込みます。SparseMatrixCSC{Int8}を返します。

デフォルトでは、ファイル拡張子が".alist"でない場合に警告を発します。（無効にするには`warn_unexpected_file_extension`を変更してください。）alist形式は冗長です（ファイルの2つの半分は、行ごとと列ごとに同じ情報を指定します）。この関数は最初の半分のみを使用します。（2番目の半分も解析して検証するには`check_redundant`を変更してください。）

alist形式の定義については、http://www.inference.org.uk/mackay/codes/alist.htmlを参照してください。
