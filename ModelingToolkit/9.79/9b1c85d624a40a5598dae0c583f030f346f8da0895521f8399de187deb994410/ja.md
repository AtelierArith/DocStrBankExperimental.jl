`@nonamespace a.b.c` を `getvar(getvar(a, :b; namespace = false), :c; namespace = false)` に書き換えます。

これは `getvar` のデフォルトの動作です。これはモデルから不明な変数を継承する際に使用するべきです。
