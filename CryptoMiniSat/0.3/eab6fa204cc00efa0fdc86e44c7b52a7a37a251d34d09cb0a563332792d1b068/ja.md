`add_clause(p::CMS, clause::Vector{Union{CMSLit,Integer}})::Bool`

システムに節を追加します。すなわち、`clause`内のエントリの論理和です。直接項は1から始まる整数で、反転項は-1から始まる負の整数です。また、`CMSLit(variable,invert)`として指定することもできます。
