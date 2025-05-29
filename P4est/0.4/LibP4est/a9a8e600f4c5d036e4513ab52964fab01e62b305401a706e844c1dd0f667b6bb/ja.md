```
sc_package_set_abort_alloc_mismatch(package_id, set_abort)
```

[`sc_package_unregister`](@ref)()の登録解除動作を設定します。

### パラメータ

  * `package_id`:[in] デフォルトパッケージの場合は-1、または登録されたパッケージの識別子でなければなりません。
  * `set_abort`:[in] [`sc_package_unregister`](@ref)()がアロケーションの数と解放の数が一致しない場合に中止すべきならtrue、そうでなければfalse。

### プロトタイプ

```c
void sc_package_set_abort_alloc_mismatch (int package_id, int set_abort);
```
