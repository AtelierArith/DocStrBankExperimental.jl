IonProperties型。

**必須キーワード**

  * `mass`: イオンの質量（kg単位）
  * `charge`: イオンの電荷（基本電荷の単位）
  * `full_level_structure`: 各エネルギーレベルの特性を記述するOrderedDict

      * `key::String`: エネルギーレベルの名前。分光学的表記を推奨、例: `"S1/2,f=1"`
      * `value::NamedTuple(:n, :l, :j, :f, :E)`: 量子数 `n`, `l`, `j`, `f` とエネルギー `E`（Hz単位）
  * `full_transitions`: エネルギーレベル間のすべての許可された遷移のDict

      * `key::Tuple{String,String}`: レベルのペア、エネルギーにおいて（下位、上位）の順
      * `value::NamedTuple(:multipole, :einsteinA)`: 遷移の主導次数の多極子（例: `"E1"`, `"E2"`）とアインシュタインA係数（微細構造レベル間のみ; ハイパーファイン因子は必要に応じて計算される）

**オプションキーワード**

  * `default_sublevel_selection`: Ionコンストラクタにおける`selected_sublevels`引数のデフォルト値
  * `gfactors`: `Dict(level::String => g::Real)` カスタムランドégファクター、一次以上の摂動からの寄与が必要な場合
  * `nonlinear_zeeman`: 特定のサブレベルのゼーマンシフトへの非線形寄与を記述する`Dict`

      * `key::Tuple{String,Real}`: サブレベル名
      * `value::Function(B::Real)`: ゼーマンシフトの非線形項。通常の線形項とこの関数の合計として完全なゼーマンシフトが計算される
