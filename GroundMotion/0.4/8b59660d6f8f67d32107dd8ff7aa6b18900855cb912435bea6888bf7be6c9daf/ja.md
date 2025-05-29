新しいGMPE PGA/強度グリッドを加重平均法を使用して計算します

**入力**

  * `config` 加重平均手順の設定
  * `grid` `gmpe_*` メソッドによるGMPEフィールドモデリング
  * `intensity_measures` 感じた報告やステーションによる強度測定
  * `intensity_in_pga` PGA %g.gg 単位での強度測定ですか？そうでない場合はSSIでの強度が想定されます。
  * `pga_out` trueに設定されている場合、関数は%g.gg 単位で修正されたGMPEフィールドを返します

**出力** `Array{Point_pga_out}` または `Array{Point_ssi_out}` の修正されたGMPEフィールド
