```julia
abstract type AbstractData{Tv}
```

ユーザーデータのための抽象型です。

ユーザーデータをAbstractDataのサブタイプにすることは可能ですが、必須ではなく、きれいに表示するshowメソッドを得ることができます。
