```
setup_ECCO4!(config::MITgcm_config)
```

ECCO4およびOCCA2ソリューションのセットアップメソッド。

```
using MITgcm

params=read_toml(:ECCO4)
folder=joinpath(pwd(),"tmp1")

MC=MITgcm_config(inputs=params,folder=folder)

#実行可能ファイルの提供（オプション）
#push!(MC.inputs[:setup][:main],(:exe => joinpath(pwd(),"mitgcmuv")))

#入力フォルダの提供（オプション）
#push!(MC.inputs[:setup][:main],(:input_folder => joinpath(pwd(),"input_folder")))

#実行時オプションの変更（オプション）
#MC.inputs[:pkg][:PACKAGES][:useECCO]=false

setup(MC)

#ビルドオプションの変更（オプション）
#MC.inputs[:setup][:build][:options]=MITgcm.build_options_pleiades

build(MC)

launch(MC)
```
