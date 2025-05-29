```
XPRSgetcontrolinfo(prob, name)::id, type
```

指定された名前の制御のID番号とタイプ情報にアクセスします。

制御名は例えば `XPRS_PRESOLVE` などです。名前は大文字と小文字を区別せず、`XPRS_` プレフィックスがある場合とない場合があります。ID番号は、XPRSgetintcontrolなどの関数呼び出しで制御を識別するために使用される定数です。名前が制御名として認識されない場合、関数は `0` のID番号と `XPRS_TYPE_NOTDEFINED` のタイプ値を返します。これは、名前が制御名ではなく属性名である場合に発生します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `name::Union{Nothing,AbstractString}`: 照会する制御の名前。

# 戻り値

  * `id::Int32`: ID番号が返される整数へのポインタ。
  * `type::XPRSParameterType`: タイプ情報が返される整数へのポインタ。

C APIの対応する関数 [XPRSgetcontrolinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcontrolinfo.html) のドキュメントも参照してください。
