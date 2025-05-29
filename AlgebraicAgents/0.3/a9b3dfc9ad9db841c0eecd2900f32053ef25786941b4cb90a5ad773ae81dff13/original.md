```
getagent(a::AbstractAlgebraicAgent, uuid::UUID)
```

Get an agent given its uuid.

## Examples

```julia
getagent(a, UUID("2a634aad-0fbe-4a91-a605-bfbef4d57f95"))
getagent(a, uuid"2a634aad-0fbe-4a91-a605-bfbef4d57f95")
```
