`(Δh(𝐻::nobleGasHeat{𝕡,𝕩},      𝒾::T_amt{𝕢,𝕪},      𝒻::T_amt{𝕣,𝕫},      B::Type{<:IntBase} = DEF[:IB])::deamt{𝕡,𝕩,B}) where {𝕡,𝕢,𝕣,𝕩,𝕪,𝕫}`

指定されたまたはデフォルトの基準における特定の熱容量でモデル化された物質の特定エンタルピーの特定のガス変化を返します。プロセスの初期温度と最終温度はそれぞれ `𝒾` と `𝒻` です。結果の精度、PREC、および正確さ、EXACは、プロモーション駆動ではなく、モデル駆動です。
