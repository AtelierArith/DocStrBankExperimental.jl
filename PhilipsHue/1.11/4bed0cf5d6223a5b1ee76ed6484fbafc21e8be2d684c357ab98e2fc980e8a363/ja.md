初めてブリッジを初期化し、デバイスタイプ（アプリ名）を指定します。このスクリプトをブリッジに登録するには、ブリッジまで走ってボタンを押す必要があるかもしれません。

返されるユーザー名は、bridge.usernameに保存されます。これは将来使用するために必要なので、覚えておくべきです。

真または偽を返します。

例えば：

```
B = PhilipsHueBridge("192.168.1.2")
initialize(bridge::PhilipsHueBridge; devicetype="juliascript#user1")
testlights(B)

# B.usernameは「2e4bdae26d734a73aeec4c21d4fd6」のようになります
```

その後、将来のJuliaセッションで次のようにできます：

```
B = PhilipsHueBridge("192.168.1.2", "2e4bdae26d734a73aeec4c21d4fd6")
testlights(B)
```
