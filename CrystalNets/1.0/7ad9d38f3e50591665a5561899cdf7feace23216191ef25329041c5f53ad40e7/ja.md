```
empty_default_archive!(; refresh=true)
```

デフォルトアーカイブを空にします。これにより、CrystalNetsは明示的に追加されるまでトポロジーを認識しなくなります。

`refresh`オプションのパラメータは、現在のアーカイブも空にするかどうかを制御します。

!!! warning
    この空のアーカイブは保持され、CrystalNets.jlの後続の実行に使用されます。Juliaセッションを再起動しても変わりません。現在のアーカイブだけを空にしたい場合は、`empty!(CrystalNets.CRYSTALNETS_ARCHIVE)`を実行してください。

