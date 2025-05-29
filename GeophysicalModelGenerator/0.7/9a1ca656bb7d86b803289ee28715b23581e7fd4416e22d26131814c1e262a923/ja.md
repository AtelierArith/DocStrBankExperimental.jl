```
save_LaMEM_markers_parallel(Grid::CartData; PartitioningFile=empty, directory="./markers", verbose=true, is64bit=false)
```

`CartData`構造体`Grid`からLaMEMマーカーファイルを保存します。`Phases`と呼ばれるフィールドを持ち、フェーズ情報（整数）を保持している必要があります。オプションで、温度情報を持つ`Temp`フィールドを持つこともできます。LaMEMパーティショニングファイル`PartitioningFile`を提供することが可能です。提供しない場合、出力は1つのプロセッサ用であると見なされます。デフォルトでは、パーティショニングファイルは32bitのPETScインストールで生成されたと仮定されます。`Int64`が代わりに使用された場合は、フラグを設定してください。

`Grid`のサイズは、LaMEM入力ファイルに提供されているものと一致している必要があります。実際には、`read_LaMEM_inputfile`を使用してLaMEM入力ファイルからメッシュのサイズを取得できます。

# 例

```
julia> Grid    = read_LaMEM_inputfile("LaMEM_input_file.dat")
julia> Phases  = zeros(Int32,size(Grid.X));
julia> Temp    = ones(Float64,size(Grid.X));
julia> Model3D = CartData(Grid, (Phases=Phases,Temp=Temp))
julia> save_LaMEM_markers_parallel(Model3D)
Writing LaMEM marker file -> ./markers/mdb.00000000.dat
```

複数のプロセッサ用のLaMEM入力ファイルを作成したい場合：

```
julia> save_LaMEM_markers_parallel(Model3D, PartitioningFile="ProcessorPartitioning_4cpu_1.2.2.bin")
Writing LaMEM marker file -> ./markers/mdb.00000000.dat
Writing LaMEM marker file -> ./markers/mdb.00000001.dat
Writing LaMEM marker file -> ./markers/mdb.00000002.dat
Writing LaMEM marker file -> ./markers/mdb.00000003.dat
```
