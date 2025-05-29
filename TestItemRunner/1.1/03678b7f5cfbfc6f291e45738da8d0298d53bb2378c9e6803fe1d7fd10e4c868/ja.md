```
@run_package_tests(ex...)
```

パッケージ内のすべてのテスト項目を実行し、オプションのフィルターおよび冗長性引数を使用します。

# 使用法

```julia
@run_package_tests filter=<filter_function>, verbose=<bool>
```

```julia
@run_package_tests filter=ti->!(:skipci in ti.tags)
```

# 引数

  * `filter`: テスト項目に適用するオプションのフィルター関数。
  * `verbose`: 冗長性を指定するオプションの引数。
