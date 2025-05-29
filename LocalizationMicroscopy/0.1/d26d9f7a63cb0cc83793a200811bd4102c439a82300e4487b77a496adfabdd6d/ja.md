```
localizationsplot(localizations::Vector{Localizations}, color::Symbol)
localizationsplot(localizations::Vector{Vector{Localization}}, colors::Vector{Symbol})
```

空間座標によってローカリゼーションをプロットします。y座標が反転していると仮定します。各軸のデフォルトは0から40960ですが、キーワード引数xlims=(x1, x2)およびylims=(y1, y2)を使用してオプションを指定できます。色はPlots.jlのドキュメントで指定されています。opacity=キーワード引数で不透明度を調整できます。factor=は、ペインでの表示や保存、印刷のために調整できます（推奨値4、デフォルト1）。
