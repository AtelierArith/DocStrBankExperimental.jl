```
rename!(df::AbstractDataFrame, vals::AbstractVector{Symbol};
        makeunique::Bool=false)
rename!(df::AbstractDataFrame, vals::AbstractVector{<:AbstractString};
        makeunique::Bool=false)
rename!(df::AbstractDataFrame, (from => to)::Pair...)
rename!(df::AbstractDataFrame, d::AbstractDict)
rename!(df::AbstractDataFrame, d::AbstractVector{<:Pair})
rename!(f::Function, df::AbstractDataFrame; cols=All())
```

`df`の列名をインプレースで変更します。各名前は最大1回変更されます。名前の順序を入れ替えることができます。

# 引数

  * `df` : `AbstractDataFrame`
  * `d` : 元の名前または列番号を新しい名前にマッピングする`AbstractDict`または`Pair`の`AbstractVector`
  * `f` : `cols`キーワード引数で選択された各列に対して、古い名前を`String`として受け取り、新しい名前を`Symbol`に変換して返す関数; `cols`列セレクタは`names`関数によって受け入れられる任意の値を指定できます
  * `vals` : `df`の列数と同じ長さの`Symbol`または`AbstractString`のベクトルとしての新しい列名
  * `makeunique` : `false`（デフォルト）の場合、重複した名前が見つかった場合にエラーが発生します; `true`の場合、重複した名前には`_i`が接尾辞として付加されます（`i`は最初の重複のために1から始まります）。

`rename!`にペアが渡されると（位置引数または辞書またはベクトル内で）:

  * `from`の値は`Symbol`、`AbstractString`、または`Integer`であることができます;
  * `to`の値は`Symbol`または`AbstractString`であることができます。

`to`と`from`でシンボルと文字列を混在させることはできません。

メタデータ: この関数はテーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。

他のスタイルのメタデータは削除されます（`df`が`SubDataFrame`の場合、親データフレームから）。列レベルの`:note`スタイルのメタデータは列番号に付随していると見なされます: 列が名前を変更されると、その`:note`スタイルのメタデータは新しい名前に関連付けられます。

参照: [`rename`](@ref)

# 例

```jldoctest
julia> df = DataFrame(i=1, x=2, y=3)
1×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(df, Dict(:i => "A", :x => "X"))
1×3 DataFrame
 Row │ A      X      y
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(df, [:a, :b, :c])
1×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(df, [:a, :b, :a])
ERROR: ArgumentError: Duplicate variable names: :a. Pass makeunique=true to make them unique using a suffix automatically.

julia> rename!(df, [:a, :b, :a], makeunique=true)
1×3 DataFrame
 Row │ a      b      a_1
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(uppercase, df)
1×3 DataFrame
 Row │ A      B      A_1
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(lowercase, df, cols=contains('A'))
1×3 DataFrame
 Row │ a      B      a_1
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

```
