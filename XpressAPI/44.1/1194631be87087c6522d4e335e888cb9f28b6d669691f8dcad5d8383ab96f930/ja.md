```
XPRSgetattribinfo(prob, name)::id, type
```

属性の名前が与えられたとき、その属性のid番号とタイプ情報にアクセスします。

属性名は例えば `XPRS_ROWS` である場合があります。名前は大文字と小文字を区別せず、`XPRS_` プレフィックスがある場合とない場合があります。id番号は、XPRSgetintattribのような関数呼び出しで属性を識別するために使用される定数です。返されるタイプ情報は、`xprs.h` ヘッダーファイルで定義された以下の整数定数のいずれかになります。名前が属性名として認識されない場合、関数はid番号0とタイプ値 `XPRS_TYPE_NOTDEFINED` を返します。これは、名前が属性名ではなく制御名である場合に発生します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `name::Union{Nothing,AbstractString}`: 照会する属性の名前。

# 戻り値

  * `id::Int32`: id番号が返される整数へのポインタ。
  * `type::XPRSParameterType`: タイプidが返される整数へのポインタ。

C APIの対応する関数 [XPRSgetattribinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetattribinfo.html) のドキュメントも参照してください。
