```
install(s::String; force::Bool = false, islocal::Bool = false)
```

URL、ディレクトリ（`islocal`がtrueの場合）、または文字列からカスタムオペレーターをインストールします。いずれの場合でも、`install`はフォルダーを/home/terasaki/.julia/packages/ADCME/94vEM/deps/CustomOps/Pluginにコピーします。`s`が文字列の場合、`s`は次のように変換されます。

https://github.com/ADCMEMarket/<s>
