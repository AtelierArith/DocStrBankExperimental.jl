```
plotisotopes(simulation::DiscretizedSPAC)
plotisotopes(simulation::DiscretizedSPAC, isotope::Symbol)
plotisotopes(simulation::DiscretizedSPAC, isotope::Symbol, (d18O = (-6, -16), d2H = (-125, -40)))
plotisotopes(simulation::DiscretizedSPAC, isotope::Symbol, (d18O = (-6, -16), d2H = (-125, -40)), RWUcentroid::Symbol))
```

SPACシミュレーションの同位体結果をプロットします。デフォルトでは両方のδ18Oとδ2Hです。ユーザーは2番目の引数isotopeを`：d18O`、`：d2H`、または`：d18O_and_d2H`のいずれかで上書きできます。RWUcentroidは`：dontShowRWUcentroid`または`：showRWUcentroid`のいずれかの値を持つことができます。
