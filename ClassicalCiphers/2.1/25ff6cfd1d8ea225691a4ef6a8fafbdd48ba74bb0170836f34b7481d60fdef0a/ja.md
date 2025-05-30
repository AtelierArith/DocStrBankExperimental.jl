```julia
crack_monoalphabetic(
    ciphertext;
    starting_key::AbstractString = "",
    min_temp::AbstractFloat = 0.0001,
    temp_factor::AbstractFloat = 0.97,
    acceptance_prob::AbstractFloat = ((e,ep,t) -> ep > e ? 1. : exp(-(e-ep)/t)),
    chatty::Integer = 0,
    rounds::Integer = 1
)
```

crack_monoalphabetic は、単一置換暗号によって暗号化された与えられた暗号文を解読します。

返されるのは `(導出された鍵, 復号化された平文)` です。

`crack_monoalphabetic` のさまざまなオプション引数は次のとおりです：

  * `starting_key=""` は、指定された場合（たとえば "ABCDEFGHIJKLMNOPQRSTUVWXYZ" のように）、与えられた鍵からシミュレーションを開始します。デフォルトでは、最も一般的な文字が最も一般的な英語の文字に復号化されるように開始します。
  * `min_temp=0.0001` は、シミュレーションを停止する温度です。
  * `temp_factor=0.97` は、各ステップで温度が減少する割合です。
  * `chatty=0` は、鍵が更新されるたびに出力するように1に設定することができるか、または新しい鍵が考慮されるたびに出力するように2に設定することができます。
  * `rounds=1` は、実行する繰り返しの回数を設定します。各ラウンドは、これまでに見つけた最良の鍵から始まります。
  * `acceptance_prob=((e, ep, t) -> ep>e ? 1 : exp(-(e-ep)/t))` は、現在の鍵の適合度が e で、温度 t のときに適合度 ep の新しい鍵を受け入れる確率です。

---

### 例

```julia
julia> crack_monoalphabetic(str, chatty=0, rounds=10)
(復号化された文字列, 鍵)
```
