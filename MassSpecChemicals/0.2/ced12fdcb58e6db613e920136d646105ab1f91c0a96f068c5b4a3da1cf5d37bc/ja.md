```
isotopologues_table(chemical::AbstractChemical, abundance = 1; abtype = :max, threshold = crit(abundance * 1e-4, 1e-4), isobaric = true, mz_tol = crit(0.01, 20e-6), mw_tol = crit(0.01, 20e-6))
isotopologues_table(formula::AbstractString, abundance = 1; abtype = :max, threshold = crit(abundance * 1e-4, 1e-4), isobaric = true, mz_tol = crit(0.01, 20e-6), mw_tol = crit(0.01, 20e-6), net_charge = 0)
isotopologues_table(tbl::Table; colchemical = :Chemical, colabundance = :Abundance, abundance = 1, colpreserve = setdiff(propertynames(tbl), [colchemical, colabundance]), kwargs...)
isotopologues_table(v::Vector, abundance = 1; kwargs...)

単一の `chemical` または `formula` の同位体分子の `Table`（`parse_chemical` によって `Chemical` に変換）、または `v` の複数の化学物質または `tbl` の列 `colchemical`。

  * `abundance` は `abtype` によって指定された同位体の存在量を設定します。

      * `:max`: 最も豊富な同位体分子
      * `:input`: 入力された同位体分子
      * その他: 最終的な存在量は比率として表されます。
  * `threshold` は数値または基準であり、存在量の下限を表します。
  * `isobaric` は同位体をグループ化し、`Isobars` を作成するかどうかを決定します。
  * `mz_tol`: 同位体の m/z の許容範囲。
  * `mw_tol`: 同位体の分子量の許容範囲。
  * `net_charge`: `formula` の電荷（正または負）。
```
