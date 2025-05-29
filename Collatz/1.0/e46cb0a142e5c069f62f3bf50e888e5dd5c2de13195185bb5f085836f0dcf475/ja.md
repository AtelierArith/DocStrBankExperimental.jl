```
stopping_time(initial_value; P=2, a=3, b=1, max_stopping_time=1000, total_stopping_time=false)
```

初期値未満の値に到達するために必要な反復回数、またはmax*stopping*timeを超えた場合は何も返さない。

また、total*stopping*timeがTrueの場合、1に到達するための反復回数をカウントします。シーケンスが停止せず、代わりにサイクルで終了する場合、結果は無限大になります。(P,a,b)がゼロにハマる可能性がある場合、結果は1に到達するための「合計停止時間」とは逆の値になります。ここで0は「合計停止」と見なされ、長さ1のサイクルを形成するため、発生すべきではありません。

# 引数

  * `initial_value::Integer`: 停止時間を求める値。

# キーワード引数

  * `P::Integer=2`: nを割るために使用されるモジュラス、nが(0 mod P)に相当する場合。
  * `a::Integer=3`: nを掛けるための係数。
  * `b::Integer=1`: nのスケーリングされた値に加える値。
  * `max_stopping_time::Integer=1000`: 停止時間に到達しない場合、関数を反復する最大回数。max*stopping*timeに到達した場合、関数は何も返しません。
  * `total_stopping_time::Bool=false`: 通常の停止時間（初期値未満の値に到達するための反復回数）ではなく、「合計」停止時間（1を取得するための反復回数）まで実行するかどうか。

# 例

```jldoctest
julia> stopping_time(5)
3
julia> stopping_time(27)
96
julia> stopping_time(21, P=5, a=2, b=3, total_stopping_time=true)
Inf
```
