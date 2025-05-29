```
create_logger!(sim::Simulation, [debug = false, name = sim.name; overwrite = sim.overwrite_file])
```

シミュレーションのログファイルを作成する標準的な方法は、[`create_simulation`](@ref) のログ記録キーワードを true に設定することです。しかし、[`copy_simulation`](@ref) の呼び出し後など、手動で制御することが有用な場合もあります。

`debug` が true に設定されている場合、ログファイルにはより多くの詳細が含まれ、各書き込み後にストリームがフラッシュされます。

`filename` 引数を使用して、`sim.filename` とは異なるファイル名を指定できます。`overwrite` が true の場合、この名前の既存のファイルは上書きされます。false の場合、ファイル名は自動的に増加する6桁の数字で拡張され、既存のファイルは上書きされません。

ファイルは常に `log` サブフォルダー内に作成され、このフォルダーは現在の作業ディレクトリに作成されます。
