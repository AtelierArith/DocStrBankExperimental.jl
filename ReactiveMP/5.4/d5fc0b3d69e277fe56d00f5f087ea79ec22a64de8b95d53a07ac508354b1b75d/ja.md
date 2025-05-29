```
AddonDebug(f :: Function)
```

このアドオンは、メッセージマッピングとプロダクトの出力に対して関数 `f` を呼び出します。結果はブール値であることが期待され、trueを返すとデバッグ情報と共にエラーがスローされます。このアドオンの一般的な用途は、メッセージや周辺分布にNaNやInfが含まれているかをチェックすることです。

## 例

```julia
checkfornans(x) = isnan(x)
checkfornans(x::AbstractArray) = any(checkfornans.(x))
checkfornans(x::Tuple) = any(checkfornans.(x))

addons = (AddonDebug(dist -> checkfornans(params(dist))),)
```
