```
stirlings2r(n::T, k::T, r::T) where T <: Integer
stirlings2r(n::T, k::T, r::T, ::Type{EqualitySampler.ExplicitStrategy})  where T <: Integer
stirlings2r(n::T, k::T, r::T, ::Type{EqualitySampler.RecursiveStrategy}) where T <: Integer

r-スターリング数の第二種を計算します。`EqualitySampler.ExplicitStrategy`（デフォルト）は明示的なループを使用し、計算効率が高いですが、オーバーフローの影響を受けるため、BigIntの使用が推奨されます。`EqualitySampler.RecursiveStrategy`は再帰を使用し、数学的には優雅ですが、大きな値に対しては非効率的です。
```
