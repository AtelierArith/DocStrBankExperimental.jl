```
load_results(bids_root::String;
    derivatives_subfolder::String="Unfold",
    lazy::Bool=false,
    generate_Xs::Bool = true,
    ses::Union{Nothing,AbstractString}=nothing,
    task::Union{Nothing,AbstractString}=nothing,
    run::Union{Nothing,AbstractString}=nothing)
```

`derivatives_subfolder`内に存在するUnfoldモデルをBIDSルートフォルダからロードします。

# キーワード

  * `derivatives_subfolder::String = "Unfold"`  bids_root/derivativesのどのサブフォルダでUnfoldモデルを探すかを定義します。
  * `lazy::Bool = false`  trueの場合、データセットをメモリに実際にロードせず、パスを含むデータフレームのみを返します。
  * `generate_Xs::Bool = true`  デフォルトではデザインマトリックスを再作成します。ロード時間を改善するためにfalseに設定できます。
  * `ses::Union{Nothing,AbstractString} = nothing`  どのセッションをロードするか; 何も指定しない場合はすべてをロードします。
  * `task::Union{Nothing,AbstractString} = nothing`  どのタスクをロードするか; 何も指定しない場合はすべてをロードします。
  * `run::Union{Nothing,AbstractString} = nothing`  どのランをロードするか; 何も指定しない場合はすべてをロードします。
