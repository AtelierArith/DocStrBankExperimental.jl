```
from_interprocedural!(interp::AbstractInterpreter, rt, sv::AbsIntState,
                      arginfo::ArgInfo, maybecondinfo) -> newrt
```

手続き間の戻り値の型 `rt` を、現在のローカル分析フレーム `sv` の文脈に適したローカルラテックス要素 `newrt` に変換します。特に：

  * `rt::LimitedAccuracy` をアンラップし、その制限を現在のフレーム `sv` に収集します。
  * ブール値 `rt` を新しいブール値 `newrt` に変換し、`newrt` が追加の条件付き洗練情報を伝播できるようにします。例えば、`rt::InterConditional` を `newrt::Conditional` に変換し、`sv` 内の変数に関する型制約情報を保持します。

この関数は、`abstract_call_method` または `abstract_call_method_with_const_args` から返された結果を伝播する場合に使用する必要があります。

`maybecondinfo !== nothing` の場合、この関数は追加の条件付き引数型洗練を試みます。そのような場合、`maybecondinfo` は次のいずれかである必要があります：

  * `maybecondinfo::Tuple{Vector{Any},Vector{Any}}`: 事前計算された引数型洗練情報
  * メソッド呼び出しシグネチャタプル型

複数の `MethodMatch` を扱う場合は、各メソッド呼び出しの引数シグネチャ型を `tmerge` して `maybecondinfo` を事前計算する方が良いです。
