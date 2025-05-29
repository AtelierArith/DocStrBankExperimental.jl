`function Base.sqrt(x::Int)::Int x; end`のような式には、以下のフィールドがあります：

  * `name::FunctionName`: 名前、`[:Base, :sqrt]`
  * `signature_hash::UInt`: メソッド宣言の型シグネチャに対して一意の`UInt`で、引数名は無視されます。この例では、`hash(ExpressionExplorer.canonalize( :(Base.sqrt(x::Int)::Int) ))`に等しく、詳細については[`canonalize`](@ref)を参照してください。
