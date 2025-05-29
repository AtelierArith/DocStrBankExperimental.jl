```
bernoulliB(n::Integer [; arr=false [, msg=true]])
```

ベルヌーイ数のインデックス `n` は、再帰関係によって定義されます。

$$
    B_n = - \frac{1}{n+1}\sum_{k=0}^{n-1}\frac{(n+1)!}{k!(n+1-k)}B_k,
$$

ここで $B_0=1$ および $B_1=-1/2$ です。$B_0$ を含めることで、*偶数インデックスの慣習* $(B_{2n+1}=0$ for $n>1)$ になります。

  * `arr` : 配列形式で出力
  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時に警告

#### 例:

```
julia> o = [bernoulliB(n) for n=0:5]; println(o)
Rational{Int64}[1//1, -1//2, 1//6, 0//1, -1//30, 0//1]

julia> o = bernoulliB(5; arr=true); println(o)
Rational{Int64}[1//1, -1//2, 1//6, 0//1, -1//30, 0//1]

julia> o = bernoulliB(big(5); arr=true); println(o)
Rational{BigInt}[1//1, -1//2, 1//6, 0//1, -1//30, 0//1]

julia> bernoulliB(60)
IOP capture: bernoulliB(60) converted to Rational{BigInt}
-1215233140483755572040304994079820246041491//56786730

julia> n = 60;
julia> bernoulliB(n; msg=false) == bernoulliB(n; msg=false, arr=true)[end]             
true
```
