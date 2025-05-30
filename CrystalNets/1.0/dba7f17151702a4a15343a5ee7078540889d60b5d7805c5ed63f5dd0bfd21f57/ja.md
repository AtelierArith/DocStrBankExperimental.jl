```
change_current_archive!(custom_arc; validate=true)
```

CrystalNets.jlが既知のトポロジーを認識するために使用する現在のアーカイブを消去し、`custom_arc`にあるファイルに保存されたアーカイブで置き換えます。

`validate`オプションのパラメータは、新しいファイルがチェックされ、CrystalNets.jlで使用可能な形式に変換されるかどうかを制御します。確信がない場合は、そのままにしておいてください。

!!! note
    この変更は、このJuliaセッションの間のみ持続します。

    デフォルトのアーカイブを変更し、以降の実行で使用したい場合は、[`clean_default_archive!`](@ref)を使用してください。


!!! warning
    無効なアーカイブを使用すると、CrystalNets.jlが使用できなくなります。この場合は、単に[`refresh_current_archive!()`](@ref)を実行してデフォルトのアーカイブに戻してください。

