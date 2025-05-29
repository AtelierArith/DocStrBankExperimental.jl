```
BootInput
```

ブートストラップ手続きを実行するために必要なすべてのパラメータを定義するコアタイプ。ほとんどのユーザーは、メソッドシグネチャを持つキーワード引数コンストラクタを使用するべきです：

```
BootInput(data ; kwargs...)
```

ここで、dataはブートストラップされるデータセットであり、kwargsは、DependentBootstrapパッケージのすべてのエクスポートされた関数で使用されるキーワード引数のセット（以下に定義）を示します。以下のキーワード引数とデフォルト値が続きます：

```
- blocklength         <- ブートストラップ手続きのブロック長。デフォルト値は0です。データセットから最適なブロック長を自動推定するには、<= 0に設定します。Float64の入力が許可されています。
- numresample         <- 入力データセットを再サンプリングする回数。デフォルト値はモジュール定数NUM_RESAMPLEで、現在1000に設定されています。
- bootmethod          <- 使用するブートストラッピング手法。デフォルト値はシンボル:stationary（定常ブートストラップ用）です。
- blocklengthmethod   <- ユーザーがブロック長を自動推定したい場合に使用するブロック長選択手続き。デフォルト値はシンボル:ppw2009（Patton、Politis、White（2009）で説明されている方法を使用）です。
- flevel1             <- 入力データセットをユーザーがブートストラップしたい推定量に変換する関数。デフォルト値はサンプル平均です。
- flevel2             <- flevel1によって構築された推定量のベクトルを分布パラメータに変換する関数。デフォルト値はサンプル分散です。
- numobsperresample   <- 再サンプリングごとに引き出される観測値の数（置換あり）。デフォルト値はデータセット内の観測値の数です（ほとんどのユーザーはこのデフォルト値を望むでしょう）。
- fblocklengthcombine <- 推定されたブロック長のVector{Float64}を単一のFloat64ブロック長推定に変換する関数。デフォルト値は中央値です。
```

コンストラクタは、提供されたすべてのキーワード引数を適切な型に変換しようとし、無効なキーワード引数が提供された場合はエラーでユーザーに通知します。

bootmethodおよびblocklengthmethodキーワード引数は、シンボルと文字列の両方の入力を受け入れ、内部的にBootMethodおよびBlockLengthMethod型に変換されることに注意してください。bootmethodおよびblocklengthmethodキーワード引数の受け入れ可能なシンボルまたは文字列の値のリストを表示するには、次を使用します：

```
- collect(keys(DependentBootstrap.BOOT_METHOD_DICT))
- collect(keys(DependentBootstrap.BLOCKLENGTH_METHOD_DICT))
```

それぞれ。少数のユーザーは、BootMethodおよびBlockLengthMethod型を明示的に構築し、それらをキーワードコンストラクタに提供することで得られる詳細な制御が必要な場合があります。これらのユーザーは、REPLで?BootMethodおよび?BlockLengthMethodを使用して詳細情報を取得するべきです。

BootInputは変更不可能ですが、タイプの構築はほぼ瞬時に行えるため、ユーザーがBootInputを修正したい場合は、別のものを構築することをお勧めします。このプロセスを容易にするために特別なコンストラクタが提供されており、メソッド定義は次のようになります：

```
- BootInput(data, bootinput::BootInput ; kwargs...)
```

ここで、新しいBootInputは提供されたキーワード引数からフィールドを引き出し、提供されていないキーワード引数については入力BootInputを使用します。

DependentBootstrapパッケージのすべてのエクスポートされた関数は、次のメソッドシグネチャを示します：

```
- exported_func(data ; kwargs...)
```

これは実際にはBootInputのキーワード引数コンストラクタをラップし、その後、メソッドシグネチャを呼び出します：

```
 - exported_func(data, bootinput::BootInput)
```
