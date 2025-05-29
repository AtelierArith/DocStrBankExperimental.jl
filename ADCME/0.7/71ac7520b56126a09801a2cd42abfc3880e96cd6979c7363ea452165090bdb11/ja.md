```
if_else(condition::Union{PyObject,Array,Bool}, fn1, fn2, args...;kwargs...)
```

  * `condition`がスカラーのブール値である場合、`condition`が真か偽かに基づいて、`fn1`または`fn2`（引数のない関数またはテンソル）を出力します。
  * `condition`がブール配列である場合、`condition .* fn1 + (1 - condition) .* fn2`を返します。

!!! info
    次のようなエラーに遭遇した場合：

    ```
    tensorflow.python.framework.errors_impl.InvalidArgumentError: Retval[0] does not have value
    ```

    `if_else`内のコードが無効である可能性があります。

