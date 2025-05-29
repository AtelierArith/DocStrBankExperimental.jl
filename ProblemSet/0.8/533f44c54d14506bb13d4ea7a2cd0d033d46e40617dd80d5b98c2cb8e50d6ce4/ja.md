```
problemset_latex(args...) -> (String,String)
```

問題と解答のlatexソースを生成します。

# 引数

  * `student_names::AbstractVector{String}`: 学生の名前
  * `problems::AbstractVector{Function}`: @problemマクロを使用して定義された関数のベクター
  * `subsets::Union{Pair,Vector{<:Pair}}`: サブセット仕様または仕様のベクター
  * `rng_seed::Integer`: 生成されたセットを再現可能にするための乱数生成器のシード
  * `set_title::String`: 問題セットのタイトル
  * `problem_title::String`: 各問題のタイトルの定数部分

サブセット仕様は、提供されたベクターから学生に割り当てる問題を選択する方法を関数に指示します。たとえば、仕様 [1=>1:3, 2=>4:7] は、最初の3つの問題の中から1つ、4から7の問題の中から2つを選択し、結果を結合します。範囲が重複する場合、ユニークな問題番号のみが保持されます。

# 例

```julia-repl
julia> student_names = ["A", "B", "C"];
julia> rng_seed = 123
julia> txt,txt_sol =  problemset_latex(student_names, my_set, 2=>1:3, rng_seed);
julia> write("problems.tex", latex_preamble*txt);
julia> write("solutions.tex", latex_preamble*txt);
```
