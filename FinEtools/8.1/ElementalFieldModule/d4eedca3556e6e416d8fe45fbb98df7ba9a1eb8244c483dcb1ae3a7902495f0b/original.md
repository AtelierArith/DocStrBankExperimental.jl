ElementalField(data::Matrix{T}, zi::IT) where {T<:Number, IT<:Integer}

Constructor of elemental field. The values of the field are given by the array on input, `data`. This array needs to have as many rows as there are elements, and as many columns as there are degrees of freedom per element.

The integer type for the storage of the degree of freedom numbers is set as that of the argument `zi`.
