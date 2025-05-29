```
@outputs(args...)
```

ユーザー出力リクエストのリストを、`Result` インスタンスに適用されたときに要求された出力を生成するファンクタのベクターに変換します。変換プロセスでは、小文字を大文字に置き換えます。

### 例

```
julia> output = @outputs FGHz θ ϕ s11db(te,te) S11ang(Te,te)
julia> output = @outputs FGHz theta phi s21db(R,H) ARdB21(H) ARdB11(v)
```
