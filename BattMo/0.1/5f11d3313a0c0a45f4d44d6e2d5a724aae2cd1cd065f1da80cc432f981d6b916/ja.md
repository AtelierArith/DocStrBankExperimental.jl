readBattMoMatlabInputFile(inputFileName::String)

Matlab出力ファイルからモデルの説明を含む入力を読み取り、シミュレーターに送信できる`MatlabInputParams`を返します。

# 引数

  * `inputFileName ::String` : 入力のファイル名

# 戻り値

シミュレーターに[`run_battery`](@ref)を介して送信できる[`MatlabInputParams`](@ref)のインスタンス。
