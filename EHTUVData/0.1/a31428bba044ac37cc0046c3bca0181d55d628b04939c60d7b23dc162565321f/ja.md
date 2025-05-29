```
load_uvfits(filename::AbstractString)::UVDataSet
```

指定されたuvfitsファイルから可視性データを読み込みます。データはPyCallによって読み込まれたastropy.io.fitsモジュールを通じて読み込まれます。
