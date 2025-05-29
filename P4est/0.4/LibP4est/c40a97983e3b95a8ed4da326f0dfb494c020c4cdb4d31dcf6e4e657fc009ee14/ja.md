```
sc_package_is_registered(package_id)
```

識別子が登録されたパッケージと一致するかどうかを照会します。

### パラメータ

  * `package_id`:[in] 非負のidのみが登録できます。

### 戻り値

パッケージidが非負であり、パッケージが登録されている場合にのみ真を返します。

### プロトタイプ

```c
int sc_package_is_registered (int package_id);
```
