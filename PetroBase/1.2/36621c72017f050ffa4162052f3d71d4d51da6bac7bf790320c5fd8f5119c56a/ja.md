このタイプは、相の最も関連性の高い特性をすべて含むように定義されており、任意の数の変数を初期化でき、デフォルトは0または空の配列/文字列になります。単位は岩石学的モデリングの便宜に基づいて選択されます。

  * `name::String`: 相の名前
  * `composition::Array{PetroBase.Component}`: 'Component' 配列によって定義された相の組成
  * `traceelements::Array{PetroBase.TraceElement}`: 相中の微量元素の濃度
  * `mol::Float64`: システム内に存在する相のモル数
  * `vol::Float64`: システム内に存在する相の体積 (J/bar [m^3/10^5])
  * `mass::Float64`: システム内に存在する相の総質量 (g)
  * `ρ::Float64`: 密度 (kg/m^3)
  * `molarmass::Float64`: モル質量 (g/mol)
  * `G::Float64`: ギブズ自由エネルギー (J/mol)
  * `H::Float64`: エンタルピー (J/mol)
  * `S::Float64`: エントロピー (J/mol)
  * `Cp::Float64`: 熱容量 (J/K·mol)
  * `Vmol::Float64`: モル体積 (J/bar·mol)
  * `Cp_Cv::Float64`: Cp/Cv (熱容量比)
  * `α::Float64`: 熱膨張係数 (1/K)
  * `β::Float64`: 圧縮率 (1/bar)
