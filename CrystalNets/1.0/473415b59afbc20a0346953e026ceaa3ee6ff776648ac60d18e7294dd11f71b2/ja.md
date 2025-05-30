```
clean_default_archive!(custom_arc; validate=true, refresh=true)
```

CrystalNets.jlが既知のトポロジーを認識するために使用するデフォルトアーカイブを消去し、`custom_arc`にあるファイルから新しいものに置き換えます。

`validate`パラメータは、新しいファイルがチェックされ、CrystalNets.jlで使用可能な形式に変換されるかどうかを制御します。確信がない場合は、そのままにしておいてください。

`refresh`オプションパラメータは、現在のアーカイブを新しいデフォルトのものに置き換えるかどうかを制御します。

!!! warning
    このアーカイブは保持され、CrystalNets.jlの次回以降の実行でも使用されます。Juliaセッションを再起動しても変わりません。

    現在のセッションのためだけにアーカイブを変更したい場合は、[`change_current_archive!(custom_arc)`](@ref change_current_archive!)を使用してください。

    同様の用途については、[`refresh_current_archive!`](@ref)も参照してください。


!!! warning
    前のデフォルトアーカイブはその後回復できないため、必要に応じてコピーを保持してください。デフォルトアーカイブは、`joinpath(dirname(dirname(pathof(CrystalNets))), "archives")`にある".arc"ファイルのセットです。

