```
fig = bodeplot(sys, args...)
bodeplot(LTISystem[sys1, sys2...], args...; plotphase=true, balance = true, kwargs...)
```

`LTISystem`(s)のボードプロットを作成します。周波数ベクトル `w` をオプションで提供できます。マグニチュードスケールを変更するには、[`setPlotScale`](@ref)を参照してください。デフォルトのマグニチュードスケールは「log10」（絶対スケール）です。

  * `hz=true`の場合、プロットのx軸はヘルツで表示され、入力周波数ベクトルは依然としてrad/sとして扱われます。
  * `balance`: プロットする前にシステムに対して[`balance_statespace`](@ref)を呼び出します。
  * `adjust_phase_start`: trueの場合、位相はシステムの積分器の過剰である`intexcess`度で-90度から始まるように調整されます。
  * `adaptive`: trueの場合、プロットされたポイントの数を少なく保ちながら、周波数応答の特徴をうまく解決するために適応周波数グリッドが使用されます。手動で提供された周波数ベクトルが使用される場合、プロット前にダウンサンプリングされることがあります。

`kwargs`はRecipesBase.plotへの引数として送信されます。
