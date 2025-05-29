```
setValue(component,
            vrs::fmi2ValueReferenceFormat,
            srcArray::AbstractArray;
            filter=nothing)
```

特定の `fmi2ScalarVariable` の値を保存し、同一の fmi2ValueReference を持つ modelVariables を含み、ステータスを示す配列を返します。

# 引数

  * `comp::FMUInstance` (FMU2Component または FMU3Instance): FMI 2 または 3 の FMU のインスタンス化されたインスタンスを表す可変構造体。
  * `vrs::fmi2ValueReferenceFormat`: ユーザーが fmi[X]ValueReference を渡す方法のワイルドカード。
  * `srcArray::AbstractArray`: 入力変数 vr (vr = vrs[i]) と同一の fmi2ValueReference を持つ modelVariables を含む `fmi2ScalarVariable` の特定の値を保存します。`srcArray` は `vrs` と同じ長さです。

# キーワード

  * `filter=nothing`: 各 ModelVariable に適用され、更新すべきかどうかを判断します。

# 戻り値

  * `retcodes::Array{fmi2Status}`: 型 `fmi2Status` の長さ `length(vrs)` の配列を返します。型 `fmi2Status` は列挙型で、関数呼び出しの成功を示します。
