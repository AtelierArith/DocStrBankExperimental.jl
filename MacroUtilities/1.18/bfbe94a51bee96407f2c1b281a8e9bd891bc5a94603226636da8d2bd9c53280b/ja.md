```
@method_def_constant [ValType=Val] [map_expr] method_call get_constant_method
```

`method_call`式が`f(::Type{T1}, ::Type{T2}, ..., ::Type{Ti}, ::ValType{::S}, ::Type{Ti+1}, ..., ::Type{Tn})`の形である場合、`get_constant_method`のメソッド定義を生成します。これは、各`f`の定義に含まれる`ValType`パラメータのすべてのコンパイル時定数を持つ要素型`S`のイテラブルを返します。

`get_constant_method`は生成された関数であり、したがってランタイムオーバーヘッドは発生しませんが、`f`の各メソッドインスタンスへのバックエッジも含まれているため、`f`の新しいメソッド定義が追加されると出力が再コンパイルされます。

`ValType`は単一のパラメータを持つシングルトン型でなければなりません。独自のカスタム型のために、最も内側の型パラメータを抽出するために`MacroUtilities.inner_param`を定義してください。

`map_expr`が提供されている場合、それは型`Vector{S}`の定数のコレクションを`Expr`にマッピングする関数に解決されなければなりません。デフォルトは`MacroUtilities.default_extract_const_expr`です。（Julia 1.7以上が必要です）
