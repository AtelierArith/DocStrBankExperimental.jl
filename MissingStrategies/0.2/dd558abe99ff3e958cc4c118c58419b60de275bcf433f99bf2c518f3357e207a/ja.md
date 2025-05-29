```
getdispatchinfo(...)
```

欠損していない型をディクショナリにディスパッチするための情報を収集します。

# 引数

[`handlemissings`](@ref)を参照してください。

# 戻り値

エントリを持つディクショナリ   

  * `dict_forig`: MacroTools.splitdef(fun)のディクショナリ結果
  * `fname_disp`: ディスパッチ関数名のシンボル、
  * `argnames`: funの引数名、
  * `kwargpasses`: キーワードパラメータ 'argname = argname' の式のベクター
  * `pos_missing`: 欠損を処理する必要がある引数の位置、
  * `type_missing`: その引数の新しい型、
  * `pos_strategy`: MissingStrategyの引数が挿入される位置、
  * `defaultstrategy`: [`MissingStrategy`](@ref)型のその引数のデフォルト
  * `suffix="_hm"`: メソッドの曖昧さを避けるために `fname_disp` に追加される番号、

これらはモジュール[`mgen`](@ref)のメソッドジェネレーターに必要な引数に一致します。
