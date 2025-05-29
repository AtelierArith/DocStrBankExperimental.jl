```
read_linelist(filename; format="vald", isotopic_abundances=Korg.isotopic_abundances)
```

リストファイルを解析し、[`Line`](@ref)のベクターを返します。

`format`キーワード引数を使用して、次のリスト形式のいずれかを指定できます（デフォルト: `"vald"`）：

  * `"vald"`は[VALD](http://vald.astro.uu.se/%7Evald/php/vald.php)リストです。これには「短い」または「長い」形式、「すべてを抽出」または「星を抽出」が含まれます。空気の波長は自動的に真空の波長に変換され、エネルギーレベルは自動的にcm$^{-1}$からeVに変換されます。
  * `"kurucz"`は原子または分子の[Kuruczリスト](http://kurucz.harvard.edu/linelists.html)です（真空波長を使用する場合はformat=kurucz_vac; Korgは2000 Å未満の波長が真空であると仮定しないため注意してください）。
  * `"moog"`は[MOOGリスト](http://www.as.utexas.edu/%7Echris/moog.html)です（広がりパラメータや解離エネルギーはサポートされておらず、真空波長であると仮定されています）。
  * `"moog_air"`は空気波長のMOOGリストです。
  * `"turbospectrum"`は空気波長の[Turbospectrumリスト](https://github.com/bertrandplez/Turbospectrum2019/blob/master/DOC/Readme-Linelist_format_v.19)です。Korgは上位または下位レベルのための（オプションの）軌道角運動量量子数lを使用しないため、ABOパラメータが利用できない場合に一般的なABOレシピにフォールバックしません。Korgの`fdamp`パラメータの解釈はTurbospectrumのものとはわずかに異なります。詳細については[`Line`](@ref)の`vdW`パラメータのドキュメントを参照してください。KorgはサポートしていないUnsoeldファッジファクターに遭遇した場合、エラーを返します。
  * "turbospectrum_vac"は真空波長のTurbospectrumリストです。
  * "korg"はKorgリスト（hdf5で保存）です。ファイル名が`.h5`で終わる場合、これがデフォルトで使用されます。

同位体情報が利用可能なVALDおよびTurbospectrumリストの場合、Korgは同位体の存在比によってlog gf値をスケーリングします（VALDがすでに事前にスケーリングしていない限り）、同位体の存在比は[NIST](https://www.nist.gov/pml/atomic-weights-and-isotopic-compositions-relative-atomic-masses)（[Korg.isotopic*abundances]）から取得します。カスタム同位体の存在比を使用するには、原子番号から原子量への存在比をマッピングする辞書を持つ`isotopic*abundances`を渡してください。

同位体の存在比のために事前にスケーリングされたリストの場合、log(gf)からの放射広がりの推定は正確ではないことに注意してください。

詳細については、[`load_ExoMol_linelist`](@ref)、[`save_linelist`](@ref)も参照してください。
