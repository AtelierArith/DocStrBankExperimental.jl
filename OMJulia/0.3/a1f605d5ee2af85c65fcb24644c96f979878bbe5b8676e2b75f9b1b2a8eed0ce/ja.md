```
sendExpression(omc, expr; parsed=true)
```

OpenModelica ZMQサーバーへのAPI呼び出しを送信します。すべての関数の完全なリストについては、[OpenModelicaユーザーガイドスクリプトAPI](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/scripting_api.html)を参照してください。

!!! note
    引数`expr`の一部の文字はエスケープする必要があります。例えば、`"`は`\"`になります。例えば、スクリプトAPI呼び出し

    ```modelica
    loadFile("/path/to/M.mo")
    ```

    は次のように変換されます。

    ```julia
    sendExpression(omc, "loadFile(\"/path/to/M.mo\")")
    ```


!!! warn
    Windowsでは、パス区切り記号`\`はエスケープする必要があります`\\`、またはUnixスタイルのパス`/`に置き換える必要があります。警告を防ぐためです。

    ```modelica
    loadFile("C:\\path\\to\\M.mo")
    ```

    は次のように変換されます。

    ```julia
    sendExpression(omc, "loadFile(\"C:\\\\path\\\\to\\\\M.mo\")")  # Windows
    sendExpression(omc, "loadFile(\"/c/path/to/M.mo\")")           # Windows
    ```


## 例

```julia
using OMJulia
omc = OMJulia.OMCSession()
OMJulia.sendExpression(omc, "getVersion()")
```
