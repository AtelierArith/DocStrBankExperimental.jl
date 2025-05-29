```
xcorr(x::AbstractVecOrMat{<:Real}, y::AbstractVecOrMat{<:Real}; demean::Bool=true, lags::AbstractVector{<:Integer}=Int[], maxlags=0)
```

2つの離散時間系列の相互相関を返します。

xが行列の場合、rはxの列のすべての組み合わせに対する自己相関および相互相関系列を含む行列です。

---

```
xcorr(x::AbstractVecOrMat{<:Real}; demean::Bool=true, lags::AbstractVector{<:Integer}=Int[], maxlags=0)
```

xの自己相関系列を返します。

相互相関は、ベクトルxとベクトルyのシフト（遅延）コピーとの類似性を遅延の関数として測定します。

### Kwargs

  * `demean`: xとyのそれぞれの平均を相互相関を計算する前に引くべきかどうかを指定します。
  * `lags`: 指定されていない場合、`maxlags=0`のときに使用される遅延は、`-min(size(x,1)-1, 10*log10(size(x,1)))`から`min(size(x,1), 10*log10(size(x,1)))`までの整数です。
  * `maxlags`: 遅延範囲を`-maxlag`から`maxlag`に制限します。
