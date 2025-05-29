```
Chairmarks.DEFAULTS
```

デフォルトのベンチマークパラメータを保持するグローバル定数です。

パラメータが指定されていない場合、`Chairmarks.DEFAULTS`に格納されている値がデフォルトとして使用されます。

現在、1つの安定したデフォルトがあります: `Chairmarks.DEFAULTS.seconds::Float64` はデフォルトで0.1です; そして1つの実験的なデフォルト: `Chairmarks.DEFAULTS.gc::Bool` はデフォルトで`true`です。

すべてのデフォルト値は将来的に変更される可能性があり、`gc`のデフォルトは完全に削除される可能性があります。
