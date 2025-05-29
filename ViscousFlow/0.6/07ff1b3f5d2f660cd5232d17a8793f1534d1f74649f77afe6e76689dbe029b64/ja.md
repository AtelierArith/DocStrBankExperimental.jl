```
setup_grid(xlim::Tuple,ylim::Tuple,phys_params::Dict[;nthreads_max=length(Sys.cpu_info())])
```

`xlim` と `ylim` の制限を持つ直交グリッドを構築し、`phys_params` のレイノルズ数によって間隔を決定します。スレッドの最大数はオプションで設定でき、デフォルトではプロセッサコアの数になります。
