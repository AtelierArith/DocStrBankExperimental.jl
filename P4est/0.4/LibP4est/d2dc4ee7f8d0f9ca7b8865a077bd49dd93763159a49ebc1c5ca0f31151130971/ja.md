```
sc_package_set_verbosity(package_id, log_priority)
```

登録されたパッケージのログの冗長性を設定します。プログラムの任意のポイントで、任意の回数呼び出すことができます。`SC_LP_THRESHOLD`の値以下に冗長性を下げることしかできません。

### パラメータ

  * `package_id`:[in] 登録されたパッケージ識別子でなければなりません。

### プロトタイプ

```c
void sc_package_set_verbosity (int package_id, int log_priority);
```
