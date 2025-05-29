```
VariableData
```

整数から文字列へのマッピングに関連するデータを格納するための不変構造体で、ソルバーは整数でのみ動作するため、変数と値の関連付けを行います。

# コンストラクタ

  * `VariableData(schedule::Schedule)::VariableData`

フィールド:

  * `divvarval_maps::OrderedDict{Symbol,OrderedDict}`: キーはシンボル `:subject` または `:teacher` です。

値は整数 (div) から整数のベクタ (var, val) の2タプルへのマップです。

  * `divvarval_mapstrs::OrderedDict{Symbol,OrderedDict}`: 整数の代わりに文字列を使用した `div_var_val_map` と同じです。
  * `alldivs::Vector{Int}`: 整数としてのすべてのdivのベクタです。
  * `allvars::Vector{Int}`: 整数としてのすべてのvarsのベクタです。 (`:subject` `:teacher` の二分割はありません)
  * `allvals::Vector{Int}`: 整数としてのすべてのvalsのベクタです。 (`:subject` `:teacher` の二分割はありません)
  * `divmap::OrderedDict{Int,String}`: div整数から文字列へのマップです。
  * `varmap::OrderedDict{Int,String}`: 変数整数から文字列へのマップです。
  * `valmap::OrderedDict{Int,String}`: 値整数から文字列へのマップです。
  * `inversedivmap::OrderedDict{String,Int}`: 逆の `divmap` です。
  * `inversevarmap::OrderedDict{String,Int}`: 逆の `varmap` です。
  * `inversevalmap::OrderedDict{String,Int}`: 逆の `valmap` です。
  * `schedule::Schedule`: スケジュールタイプのインスタンスです。
