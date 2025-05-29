IonInstance(selected_sublevels::Vector{Tuple}[, manualshift::Dict]) イオンのインスタンス

`selected_sublevels` は、このイオンインスタンスのヒルベルト空間に存在するエネルギーサブレベルを、すべての可能なサブレベルのサブセットとして指定します。

`selected_sublevels` の各要素は、2要素のタプル `(level::String, sublevels)` であり、最初の要素はレベルの名前で、2番目の要素は含めるべきサブレベルを指定します。許可されるサブレベルは、磁気量子数 `m` が {`-f`, `-f+1`, `-f+2`, ... `f-1`, `f`} のセットに含まれるものであり、ここで `f` は `level` の全角運動量量子数です。指定された各 `level` に対して、含める `sublevels` のセットを指定するための3つの許可されたオプションがあります：

  * `sublevels::Real`: 単一の `m = sublevels` のみを含めます
  * `sublevels::Vector{Real}`: 磁気量子数 `m` が `sublevels` に含まれるすべてのサブレベルを含めます
  * `sublevels = "all"`: すべての許可されたサブレベルを含めます

`selected_sublevels` の要素が最初のオプションを利用して単一の `m` を指定する場合、オプションでこれを3要素のタプル `(level::String, m::Real, alias::String)` にすることができ、この特定のサブレベルにエイリアス `alias` を割り当てます。

`selected_sublevels` にレベルが省略されると、すべてのサブレベルが除外されます。

**フィールド**

  * `speciesproperties::IonProperties`: 種に特有のパラメータを指定する定数を含みます
  * `sublevels`::Vector{Tuple{String,Real}}: ヒルベルト空間に存在するすべてのサブレベルのリスト
  * `sublevelaliases::Dict{String,Tuple}`: サブレベルに割り当てられたエイリアスを指定する辞書、形式は `alias => sublevel`
  * `shape`::Vector{Int}: ヒルベルト空間の次元
  * `manualshift::OrderedDict`: 選択されたレベルを示すキーと、レベルのエネルギーのシフトを記述する実数値を持つ辞書。これは、ヒルベルト空間に存在しないエネルギーレベルからのスタークシフトなど、シミュレーションに手動シフトを追加するための便利な方法です
  * `ionnumber`: イオンが `IonTrap` に追加されると、この値はその順序を追跡します
  * `ionposition`: イオンが `IonTrap` に追加されると、この値はメートル単位での物理的位置を追跡します
