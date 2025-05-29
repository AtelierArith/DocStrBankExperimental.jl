```
agg!(R::AbstractArray{FT,3}, A::AbstractArray{<:Real,3}; 
    fact=2, parallel=true, fun=mean)
agg(A::AbstractArray{<:Real,3}; fact=2, parallel=true, fun=mean)
```

3次元配列 `A` を時間次元（3次元目）で `fact` の因子で集約し、関数 `fun` を使用します。
