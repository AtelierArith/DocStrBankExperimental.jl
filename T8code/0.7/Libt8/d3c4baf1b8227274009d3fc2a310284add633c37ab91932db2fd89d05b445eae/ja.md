```
t8_cmesh_set_profiling(cmesh, set_profiling)
```

cmeshのプロファイリングを有効または無効にします。プロファイリングが有効な場合、cmesh_commit中に実行時間と統計が収集されます。

プロファイリングはデフォルトで無効です。この関数を呼び出す前にcmeshをコミットしてはいけません。

# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `set_profiling`:[in] trueの場合、プロファイリングが有効になり、falseの場合は無効になります。

# 参照

[`t8_cmesh_print_profile`](@ref)

### プロトタイプ

```c
void t8_cmesh_set_profiling (t8_cmesh_t cmesh, int set_profiling);
```
