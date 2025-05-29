空間内で新しい座標フレームを定義するための簡単な便利マクロです。最終引数である `property` の新しい `abstract` サブタイプを作成します。

# 拡張ヘルプ

**使用法**

`@frame <name>` `@frame <name> is <property>`

ここで、`<property>` は以前に定義された `OrbitalFrame` であり、すべて `OrbitalFrames.OrbitalFrame` のサブタイプでなければなりません。短縮構文 `@frame <name>` を使用することで、新しい `abstract` 型 `<name>` は `supertype` として `OrbitalFrames.OrbitalFrame` のみを持つことになります。

**例**

```julia
@frame AbstractFrame # 第二引数はトップレベルの `OrbitalFrame` にデフォルト設定されます
@frame EarthCenteredInertial is BodycentricInertial
@frame SunEarthSynodic is BarycentricInertial
```
