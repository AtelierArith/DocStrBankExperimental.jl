```
save_at(worker, sym, val)
```

値 `val` を `worker` のシンボル `sym` に保存します。`sym` は引用符で囲む必要があります（またはシンボルを含む必要があります）。`val` は処理中にアンコートされ、ワーカーで評価されます。ワーカーに正確なコマンドを渡したい場合は、引用符で囲んでください。

これはおおまかにパッケージ ParallelDataTransfers に基づいていますが、明示的なフェッチなどを省略/遅延させることで、少し柔軟に作られています。特に、`save_at` はおおよそ `ParallelDataTransfers.sendto` と同じであり、`get_val_from` は `ParallelDataTransfers.getfrom` と非常に似ています。

# 戻り値

操作が完了したことを確認するために取得できる Nothing の未来。

# 例

```
addprocs(1)
save_at(2,:x,123)       # 123 を保存
save_at(2,:x,myid())    # 1 を保存
save_at(2,:x,:(myid())) # 2 を保存
save_at(2,:x,:(:x))     # シンボル :x を保存
                        # (ただの :x はアンコートのため機能しません)
```

# 注意: シンボルのスコープ

シンボルは対応するワーカーの Main モジュールに保存されます。たとえば、`save_at(1, :x, nothing)` はあなたのローカル `x` 変数を消去します。名前の衝突に注意してください。
