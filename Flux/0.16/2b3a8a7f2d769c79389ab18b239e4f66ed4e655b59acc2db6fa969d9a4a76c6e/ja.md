```
create_bias(weights, bias, size...)
```

レイヤーのバイアスパラメータを返します。これは、コンストラクタのキーワード `bias=bias` に与えられた値に基づいています。

  * `bias == true` は、与えられたサイズのトレーニング可能な配列を作成し、`weights` と同じ型で、初期値はゼロです。
  * `bias == false` は `false` を返し、これはADによって非微分可能であると理解されます。
  * `bias::AbstractArray` は、提供された配列を使用しますが、正しいサイズである必要があります。また、`eltype` を `weights` と一致するように修正します。
