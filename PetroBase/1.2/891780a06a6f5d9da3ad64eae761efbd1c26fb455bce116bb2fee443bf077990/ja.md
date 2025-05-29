このタイプは、岩石学的システムの最も関連性の高い特性をすべて含むように定義されており、任意の数の変数を初期化でき、デフォルトは0または空の配列/文字列になります。単位は岩石学的モデリングの便宜に基づいて選択されます。

  * `composition::Array{PetroBase.Component}`: 'Component' 配列によって定義されたシステムの組成
  * `phases::Array{PetroBase.Phase}`: システム内の相
  * `traceelements::Array{PetroBase.TraceElement}`: システム内の微量元素の濃度
  * `mol::Float64`: システム内のすべての成分の総モル数
  * `vol::Float64`: システム内のすべての相の総体積 (J/bar [m^3/10^5])
  * `mass::Float64`: システムの総質量 (g)
  * `ρ::Float64`: システムの密度 (kg/m^3)
  * `molarmass::Float64`: システムのモル質量 (kg/m^3)
  * `G::Float64`: ギブズ自由エネルギー (J/mol)
  * `H::Float64`: エンタルピー (J/mol)
  * `S::Float64`: エントロピー (J/K·mol)
  * `Cp::Float64`: 熱容量 (J/K·mol)
  * `Vmol::Float64`: モル体積 (J/bar·mol)
  * `Cp_Cv::Float64`: Cp/Cv (熱容量比)
  * `α::Float64`: 熱膨張係数 (1/K)
  * `β::Float64`: 圧縮率 (1/bar)
