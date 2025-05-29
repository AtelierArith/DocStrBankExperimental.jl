```
FieldArray(
    fr::FieldRecord; 
    expand_cartesian=true, 
    omit_recorddim_if_constant=true,
    lookup_coords=true,
    coords=nothing,
)
```

[`FieldArray`](@ref)を`fr::FieldRecord`内のすべてのレコードから構築します。

`FieldRecord`の内部ストレージ形式のビューをn次元配列として提供します。

# キーワード引数

  * `expand_cartesian`: （`CartesianLinearGrid`を使用した空間的に解決された出力のみ）、圧縮された内部データ（空間次元`cells`を持つ）を空間次元（例えば`lon`、`lat`、`zt`）を持つカートesian配列に展開するために`true`。
  * `omit_recorddim_if_constant`: 定数変数（属性`is_constant = true`を持つ）のために、複数の（同一の）レコードとレコード次元を含めるかどうかを指定します。PALEOは現在、これらのレコードを入力`fr::FieldRecord`に常に保存します。`false`を設定すると、`FieldArray`の出力にそれらを含め、`true`を設定すると、出力から重複レコードとレコード次元を省略します。
  * `lookup_coords`: 座標を含めるために`true`、座標を省略するために`false`。
  * `coords`: 入力`fr::FieldRecord`から1つ以上の次元の付随する座標を置き換えます。形式は`"<dim_name>"=>("<var_name1>", "<var_name2>", ...)`のペアのベクターです。例えば、nDカラム大気モデルのデフォルトの圧力座標をz座標で置き換えるには：

    ```
    coords=["cells"=>("atm.zmid", "atm.zlower", "atm.zupper")]
    ```
