```
simulate!(mechanism, steps, storage, control!;
    record, verbose, abort_upon_failure, opts)

メカニズムをシミュレートする

mechanism: メカニズム 
steps: シミュレートするステップの範囲 
storage: ストレージ
control!: メカニズムの入力を設定する関数
record: ストレージにシミュレーションを記録するためのフラグ
verbose: シミュレーション中に出力するためのフラグ 
abort_upon_failure: ソルバーが許容誤差を満たさない場合にシミュレーションを終了するためのフラグ
opts: SolverOptions
```
