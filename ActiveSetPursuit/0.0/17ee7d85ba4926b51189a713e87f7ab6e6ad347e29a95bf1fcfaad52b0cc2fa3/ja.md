`julia     function bpdual(A, b, λin, bl, bu; kwargs...)` 

````
最適化問題を解く:

DP:
```math 
    \min_{y} \left( -b^T y + \frac{1}{2} λ y^T y \right)
```
    制約条件:
 ```math 
    bl \leq A^T y \leq bu
    ```

与えられた `A`, `b`, `bl`, `bu`, および `λ` を使用して。`bl = -e` および `bu = e = ones(n, 1)` のとき、
DP は双対基追求問題です:

BPdual:

```math 
\max_{y} \left( b^T y - \frac{1}{2} λ y^T y \right)
```
    制約条件
    
```math
    \|A^T y\|_{\infty} \leq 1.
```

* 入力
* `A` : `m`-by-`n` 明示的行列または線形演算子。
* `b` : `m`-ベクトル。
* `λin` : 非負スカラー。
* `bl`, `bu` : `n`-ベクトル (bl 下限, bu 上限)。
* `active`, `state`, `y`, `S`, `R` : 空であるか、以前の `λ` の値を持つ `BPdual` からの出力。
* `loglevel` : ロギングレベル。
* `coldstart` : コールドスタートを使用するかどうかを示すブール値。
* `homotopy` : ホモトピーを使用するかどうかを示すブール値。
* `λmin` : `λ` の最小値。
* `trim` : 削除する制約の数。
* `itnMax` : 最大反復回数。
* `feaTol` : 実現可能性の許容誤差。
* `optTol` : 最適性の許容誤差。
* `gapTol` : ギャップの許容誤差。
* `pivTol` : ピボットの許容誤差。
* `actMax` : アクティブ制約の最大数。

* 出力
* `tracer` : 最適化プロセスの各反復でトレース情報を保存する構造体。
    含まれるもの:
        * `active::Vector{Int}`: アクティブ制約のインデックス。
        * `activesoln::Vector{T}`: 現在のアクティブセットに対応する解。
        * `lambda::Vector{T}`: ラムダ値。
        * `N::Int`: 解ベクトル内の変数の総数。
````
