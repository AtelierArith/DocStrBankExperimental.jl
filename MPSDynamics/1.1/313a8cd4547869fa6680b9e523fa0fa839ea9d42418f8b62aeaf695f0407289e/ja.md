```
runsim(dt, tmax, A, H; 
	method=:TDVP1, 
	machine=LocalMachine(), 
	params=[], 
	obs=[], 
	convobs=[],
            convparams=error("収束パラメータを指定する必要があります"),
            save=false,
            plot=save,
            savedir=string(homedir(),"/MPSDynamics/"),
            unid=randstring(5),
            name=nothing,
	kwargs...
	)
```

MPS `A` を MPO `H` で時間 `tmax` まで `dt` の時間ステップで伝播させます。最終的な MPS は `A` に返され、測定データは `dat` に返されます。

# 引数

  * `method`: MPSDynamics ではいくつかのメソッドが実装されています。 `:TDVP1` はツリーおよびチェーン MPS における 1サイト TDVP を指し、 `:TDVP2` はチェーン MPS における 2サイト TDVP を指し、 `:DTDVP` はチェーン MPS における動的ボンド次元を持つ 1サイト TDVP の変種を指します。
  * `machine`: `LocalMachine()` はローカルリソースを指し、 `RemoteMachine()` は遠隔リソースを指します。
  * `params`: 動的を説明するために log.txt ファイルに書き込まれるパラメータのリスト。 @LogParams() でリストできます。
  * `obs`: 最も正確な収束パラメータ `convparams` に供給されるため、各時間ステップで測定される可観測量のリスト。
  * `convobs`: 各収束パラメータ `convparams` に供給されるため、各時間ステップで測定される可観測量のリスト。
  * `convparams`: 各パラメータに対して伝播が計算される収束パラメータのリスト。各パラメータで `convobs` が測定され、 `obs` は最も正確な動的に対してのみ測定されます。
  * `save`: データがファイルに保存されるかどうかを選択するために使用されます。
  * `plot`: 1D 可観測量のプロットが自動的に生成され、データと共に保存されるかどうかを選択するために使用されます。
  * `savedir`: 結果ファイルが保存されるパスを指定するために使用されます。
  * `unid`: 結果ファイルを含むディレクトリの名前を指定するために使用されます。
  * `name`: 計算を説明するために使用されます。この名前は log.txt ファイルに表示されます。
