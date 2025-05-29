Abstract type for morphism in the category **Set**.

Every instance of `SetFunction{<:SetOb{T},<:SetOb{T′}}` is callable with elements of type `T`, returning an element of type `T′`.

Note: This type would be better called simply `Function` but that name is already taken by the base Julia type.
