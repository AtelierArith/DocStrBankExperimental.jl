```
plothistory(tsol; 
            plots=[:timestepsizes,
                   :timestepupdates,
                   :newtonsteps,
                   :newtonupdates], 
            size=(700,600), 
            logmin=1.0e-20,
            Plotter=GridVisualize.default_plotter(),
            kwargs...)
```

`tsol`に保存された解の履歴をプロットします。`plots`引数を使用して、表示するプロットを選択できます。
