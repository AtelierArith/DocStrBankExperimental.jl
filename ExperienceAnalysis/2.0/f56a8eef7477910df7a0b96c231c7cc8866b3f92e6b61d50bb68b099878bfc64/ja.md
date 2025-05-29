```
exposure(
    p::Anniversary,
    from::Date,
    to::Date,
    continued_exposure::Bool = false;
    study_start=typemin(from),
    study_end=typemax(from),
    left_partials::Bool=true,
    right_partials::Bool=true,
)::Vector{NamedTuple{(:from, :to, :policy_timestep),Tuple{Date,Date,Union{Int,Nothing}}}}
```

曝露期間を計算し、以下のフィールドを持つ名前付きタプルの配列を返します：

  * `from`（`Date`型）は曝露区間の開始日です
  * `to`（`Date`型）は曝露区間の終了日です
  * `policy_step`は、AnniversaryまたはAnniversaryCalendarの基準が使用されている場合は`Int`になります。それ以外の場合は`nothing`になります

`continued_exposure`が`true`の場合、最終的な`to`日付は最終曝露期間の終了まで続きます。これは、関心の減少が終了の原因である場合に完全な曝露を望むために便利です。

`left_partials`または`right_partials`がfalseに設定されている場合、曝露はそれぞれ`study_start`および`study_end`と重なる部分的な曝露期間を返しません。

# 例

```julia-repl julia> using ExperienceAnalysis,Dates julia> exposure(     ExperienceAnalysis.Anniversary(Year(1)), # basis     Date(2020,5,10),                         # issue     Date(2022, 6, 10);                       # termination ) 3-element Vector{NamedTuple{(:from, :to, :policy*timestep), Tuple{Date, Date, Int64}}}:  (from = Date("2020-05-10"), to = Date("2021-05-09"), policy*timestep = 1)  (from = Date("2021-05-10"), to = Date("2022-05-09"), policy*timestep = 2)  (from = Date("2022-05-10"), to = Date("2022-06-10"), policy*timestep = 3)

```
