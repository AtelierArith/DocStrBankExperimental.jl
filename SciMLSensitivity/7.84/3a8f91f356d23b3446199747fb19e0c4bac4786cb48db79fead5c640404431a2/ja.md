```julia
ZygoteVJP <: VJPChoice
```

Zygote.jlを使用してベクトル-ヤコビ行列積を計算します。ODE/DAE/SDE/DDEが主にベクトル化された関数（ニューラルネットワークやFlux.jlの他のレイヤーのような）で書かれている場合、最も高速なVJPメソッドになる傾向があります。また、`f`関数がアウトオブプレースで与えられる必要があります。`f`関数がインプレースの場合、内部で`Zygote.Buffer`配列が使用され、VJPメソッドのパフォーマンスが大幅に低下する可能性があります。

## コンストラクタ

```julia
ZygoteVJP(; allow_nothing = false)
```

キーワード引数：

  * `allow_nothing`: `nothing`が暗黙的にゼロに変換されるべきかどうか。Zygoteでは、`p`を使用しない関数の導関数は、ゼロの代わりに`nothing`が与えられます。デフォルトでは、この`nothing`は、意図しない誤定義関数に関する情報メッセージをスローするためにキャッチされます。しかし、これが意図的であった場合、`allow_nothing=true`を設定することでエラーメッセージを削除できます。
