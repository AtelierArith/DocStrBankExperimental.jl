```
stieltjes(n)
```

最初の10個のStieltjes（一般化されたオイラー・マスケローニ）定数を提供します（参照：Abramowitz and Stegunm, 23.2.5）または[https://en.wikipedia.org/wiki/Stieltjes_constants](https://en.wikipedia.org/wiki/Stieltjes_constants)。

「一般化されたオイラー・マスケローニ定数」という表があり、O.R. AinsworthとL.W. HowellによるNASA技術論文2264、1984年1月の[https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/19840007812.pdf](https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/19840007812.pdf)ですが、OEISにはより正確な値があり、これは私がビットフロートバージョンのコードに取り組むときに役立ちます。

stieltjes(0) = γ、オイラー・マスケローニ定数、または単にオイラーの定数とも呼ばれることに注意してください。[https://en.wikipedia.org/wiki/Euler-Mascheroni_constant](https://en.wikipedia.org/wiki/Euler%E2%80%93Mascheroni_constant)

## 引数

  * `n::Integer`: 計算する要素の数。

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> stieltjes(0)
0.5772156649015329
```
