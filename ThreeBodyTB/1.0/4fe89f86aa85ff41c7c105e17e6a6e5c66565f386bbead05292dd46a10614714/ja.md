```
function set_bin_dirs(;qe=missing, mpi=missing, pseudodir=missing, templatedir=missing, wannier=missing)
```

量子エスプレッソのバイナリがあるディレクトリを設定します。すべてが指定されていない場合は、現在のディレクトリを表示します。

  * `qe` - 量子エスプレッソのバイナリディレクトリを設定します。pwとppがインストールされている必要があります。便利なデフォルトはありません。
  * `mpi` - mpiコマンドを設定します。例えば「mpirun -np 」のようなものです。
  * `pseudo` - 擬似ポテンシャルのディレクトリを設定します。デフォルトはこのコードに付属している../pseudo/gbrv_pbesol/を使用します。
  * `template` - 量子エスプレッソのテンプレートファイルのディレクトリを設定します。デフォルトでは../template_inputs/を使用します。
