```
sync_workgroup_or(predicate::Cint)::Cint
```

`sync_workgroup`と同じですが、追加機能として、ワークグループ内のすべてのワークアイテムに対して述語を評価し、いずれかのワークアイテムに対して述語が非ゼロである場合にのみ非ゼロを返します。
