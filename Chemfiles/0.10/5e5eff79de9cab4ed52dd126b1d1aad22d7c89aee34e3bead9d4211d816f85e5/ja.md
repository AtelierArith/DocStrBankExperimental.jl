```julia
close(trajectory::Chemfiles.Trajectory)

```

`trajectory`を閉じます。この関数は、バッファの内容をハードドライブにフラッシュし、関連するメモリを解放します。REPLで実行しているときに書き込みを完了するために必要です。
