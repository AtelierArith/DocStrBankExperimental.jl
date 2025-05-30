cmdstanの実行可能ファイル（`bin/stanc`や`bin/stansummary`など）が含まれているディレクトリ。

# 拡張ヘルプ

利用可能な場合、環境変数`CMDSTAN`または`ENV["CMDSTAN"]`から推測されます。

これらが利用できない場合は、`set_cmdstan_home!`を使用してCMDSTAN_HOMEの値を設定します。

例: `set_cmdstan_home!(homedir() * "/Projects/Stan/cmdstan/")`

`versioninfo()`を実行すると、定義されている場合は`CMDSTAN`の値が表示されます。
