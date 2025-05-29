```
Line(wl::F, log_gf::F, species::Species, E_lower::F,
     gamma_rad::Union{F, Missing}=missing, gamma_stark::Union{F, Missing}=missing,
     vdw::Union{F, Tuple{F, F}, Missing}, missing) where F <: Real
```

引数:

  * `wl`: 波長 (1未満の場合はcm、そうでない場合はÅと仮定)
  * `log_gf`: (底10の) オシレーター強度 (単位なし)
  * `species`: 行に関連する `Species`
  * `E_lower`: 下位エネルギーレベルのエネルギー (励起ポテンシャル) (eV)

オプション引数 (これらはデフォルトレシピを上書きします):

  * `gamma_rad`: 基本幅
  * `gamma_stark`: 10,000 Kにおける摂動ごとのスタークブロードニング幅 (s⁻¹)。
  * `vdW`: これが存在する場合、次のようになる可能性があります。

      * `log10(γ_vdW)`、負の場合は仮定されます
      * 0、vdWブロードニングなしに対応
      * Unsoeld近似のためのファッジファクター、0と20の間の場合は仮定されます
      * [ABOパラメータ](https://github.com/barklem/public-data/tree/master/broadening-howto)としてパックされた浮動小数点 (20以上の場合は仮定) または `Tuple`、`(σ, α)`。

    この動作は、Turbospectrumの動作をできるだけ忠実に反映することを意図しています。

`gamma_stark` と `vdW` のデフォルトレシピに関する詳細は、[`approximate_gammas`](@ref)を参照してください。

ここでの「gamma」値はFWHMであり、HWHMではなく、線プロファイルのローレンツ成分のもので、単位はs⁻¹です。

```
Line(line::line; kwargs...)
```

既存の `Line` から値をコピーして新しい `Line` を構築します。任意の値はキーワード引数で変更できます。例: `Line(line, log_gf=0.0)`。
