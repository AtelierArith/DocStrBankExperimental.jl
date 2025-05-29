```
getSimpleTypeAttributeStruct(st::fmi2SimpleType)
```

単純型 `st` の属性構造体を返します。定義に応じて、これは `st.Real`、`st.Integer`、`st.String`、`st.Boolean` または `st.Enumeration` のいずれかです。

# 引数

  * `st::fmi2SimpleType`: カスタム SimpleTypes に関する情報を提供する構造体。

# 出典

  * FMISpec2.0.3 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.3[p.40]: 2.2.3 型の定義 (TypeDefinitions)
