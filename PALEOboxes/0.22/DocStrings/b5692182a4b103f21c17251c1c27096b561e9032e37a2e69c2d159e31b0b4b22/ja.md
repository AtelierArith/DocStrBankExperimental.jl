```
DocStrings
```

Juliaの`DocStringExtensions`パッケージを拡張して、ドキュメント文字列に反応パラメータと変数をリストするためのPALEO特有の「略語」を提供します。

`PARS`、`METHODS*SETUP`、`METHODS*INITIALIZE`、`METHODS_DO`をエクスポートします。

`$(PARS)`は反応パラメータのリストに展開され、`$(METHODS_SETUP)`、`$(METHODS_INITIALIZE)`、`$(METHODS_DO)`は反応メソッドと変数のリストに展開されます。

注意: 反応は`create_reaction`で作成されます。さらに、`$(METHODS_DO)`などは`register_methods(rj::AbstractReaction)`を呼び出すため、デフォルトパラメータでこの呼び出しが失敗すると失敗する可能性があります。
