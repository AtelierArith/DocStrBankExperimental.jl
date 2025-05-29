```
XPRSnlpadduserfunctionvecmap(prob, funcname, nin, options, func)::type
```

SLP問題にユーザー関数の定義を追加します。

`func`はこのシグネチャで呼び出されます。

```
function(values::AbstractVector{Cdouble})::Cdouble
```

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `funcname::Union{Nothing,AbstractString}`: テキスト数式表現に表示される関数の名前。
  * `nin::Integer`: ユーザー関数が取る引数の数。
  * `options::Integer`: ユーザー関数に対するビットマップとしてのオプション。XSLP_INSTANCEFUNCTIONは常に関数をインスタンス化します。
  * `func::Function`: 呼び出すユーザー関数のポインタ。

# 戻り値

  * `type::Int32`: 追加されたユーザー関数のトークンID。数式を定義し、`XSLP_FUN`と共に使用する際に使用されます。

対応する関数のドキュメントも参照してください [XPRSnlpadduserfunction](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpadduserfunction.html) C APIにおいて。
