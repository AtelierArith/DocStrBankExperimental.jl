```julia
load_ldpc_from_json(
    file_path;
    expand_qc_exponents_to_binary
)

```

LDPC行列を、圧縮スパース列（CSC）ストレージを含むjsonファイルから読み込みます。

  * `qccscjson`（準周期指数のCSC）形式
  * `bincscjson`（スパースバイナリ行列のCSC）形式

準周期指数を展開してスパースバイナリ行列を取得するオプションを使用します。
