```
JUA_Argument
```

`JUA_Argument`オブジェクトを定義する可変構造体 - `UA_Argument`の同等物ですが、CではなくJuliaによってメモリが管理されます（以下の例外を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_Argument()
```

空の`JUA_Argument`を作成します。これは`UA_Argument_new()`を呼び出すのと同等です。

```
JUA_Argument(examplearg::Union{Nothing, AbstractArray{<: ARG_TYPEUNION}, ARG_TYPEUNION} = nothing; 
        name::Union{Nothing, AbstractString} = nothing, 
        description::Union{AbstractString, Nothing} = nothing, 
        localization::AbstractString = "en-US",
        datatype::Union{Nothing, ARG_TYPEUNION} = nothing,
        valuerank::Union{Integer, Nothing} = nothing, 
        arraydimensions::Union{Integer, AbstractArray{<: Integer}, Nothing} = nothing)
```

`examplearg`のプロパティに基づいて`JUA_Argument`を作成します。具体的には、`datatype`、`valuerank`、および`arraydimensions`は`examplearg`から自動的に決定されます。`name`、`description`、および`localization`のキーワード引数を使用して`JUA_Argument`をさらに説明できます。

`valuerank`と`arraydimensions`のプロパティについては、こちらを参照してください: [OPC Foundation Website](https://reference.opcfoundation.org/Core/Part3/v105/docs/8.6)

```
JUA_Argument(argumentptr::Ptr{UA_Argument})
```

ポインタ`argumentptr`に基づいて`JUA_Argument`を作成します。これは、低レベルインターフェースを介して生成された`UA_Argument`を高レベル関数に渡すために使用できるフォールバックメソッドです。このメソッドを使用する際は、メモリ管理がC側に残ることに注意してください。つまり、オブジェクトが不要になった後に`UA_Argument_delete(argumentptr)`で`argumentptr`を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。

例：

```
j = JUA_Argument()
j = JUA_Argument(1.0) #Float64スカラーを受け入れます
j = JUA_Argument(zeros(Float32, 2, 2)) #サイズ2x2のFloat32配列のみを受け入れます
j = JUA_Argument(zeros(Float32, 2, 2), arraydimensions = [0, 0]) #任意の2D Float32配列を受け入れます。
j = JUA_Argument(datatype = Int8, valuerank = 1, arraydimensions = [2, 2]) #サイズ2 x 2のInt8配列を受け入れます。
j = JUA_Argument(datatype = Float64, valuerank = 1, arraydimensions = 4) #4要素のFloat64ベクトルを受け入れます。
j = JUA_Argument(datatype = Float64, valuerank = 1, arraydimensions = 0) #任意の長さのFloat64ベクトルを受け入れます。
```
