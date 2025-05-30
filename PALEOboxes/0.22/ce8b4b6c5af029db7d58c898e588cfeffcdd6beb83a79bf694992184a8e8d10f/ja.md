```
add_method_setup_initialvalue_vars_default!(react::AbstractReaction, variables [; kwargs...])
```

`filterfn` に一致する変数を初期化するデフォルトメソッドを作成して追加します（デフォルトは状態変数）統合の開始時に。

# 使用されるコールバックのセットアップ

  * 状態変数および類似のもの（`:vfunction != VF_Undefined`）は、`attribute_name in (:initial_value, :norm_value)` を使用してセットアップコールバックで初期化され、これらの変数属性からの値が使用されます。
  * `force_state_norm_value=false` の場合、他の変数（`:vfunction == VF_Undefined`）は、`attribute_name=:setup` を使用してセットアップコールバックで初期化され、`:initial_value` 変数属性からの値が使用されます。注意：`filterfn` はこれらの変数を含むように設定する必要があります。
  * `force_initial_norm_value=true` の場合、すべての変数（`:vfunction == VF_Undefined` のものを含む）は状態変数として初期化されます。

# キーワード

  * `filterfn`: 状態変数のみのデフォルト選択をオーバーライドするために f(var)::Bool に設定します（`:vfunction in (VF_StateExplicit, VF_State, VF_Total, VF_StateTotal, VF_Constraint)` の変数）。
  * `force_initial_norm_value=false`: `true` に設定すると、`:vfunction=VF_Undefined` の変数に対しても常に `:initial_value`, `:norm_value` を使用します。
  * `transfer_attribute_vars=[]`: `variables` と同じ長さのリストに設定して、`transfer_attribute_vars` の属性から `variables` を初期化します。
  * `setup_callback=(method, attribute_name, var, vardata) -> nothing`: 各変数の初期化後に呼び出される関数に設定します。例：ノルム値を保存するため。
  * `convertvars=[]`
  * `convertfn = (convertvars_tuple, i) -> 1.0`
  * `convertinfo = ""`

# 体積などの変換を含む

`convertvars` を変数のベクター（例：細胞体積）に設定し、`convertfn` と `convertinfo` を提供して、`VarList_tuple(convertvars)` によって生成されたタプルの引数で `:initial_value*convertfn(convertvars_tuple, i)` に初期化します。

例：`:initial_value` を濃度のような量として解釈するため：

```
convertvars = [volume], 
convertfn = ((volume, ), i) -> volume[i], 
convertinfo = " * volume"
```
