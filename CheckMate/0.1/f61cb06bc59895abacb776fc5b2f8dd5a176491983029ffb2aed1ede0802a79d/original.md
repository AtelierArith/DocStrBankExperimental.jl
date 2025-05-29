```
@checkset(name::String, block::Expr)::CheckSet
```

Create a named set of data validation checks.

# Arguments

  * `name`: A descriptive name for the set of checks
  * `block`: A block of check definitions using @check syntax

# Examples

```julia
# Define your check functions
function check_amount_positive(amount)
    amount > 0
end

function check_valid_currency(currency)
    currency in ("USD", "EUR", "GBP")
end

# Create a checkset
checks = @checkset "Payment Validation" begin
    @check "Amount is positive" check_amount_positive(:amount)
    @check "Valid currency" check_valid_currency(:currency)
end
```

Note: Check conditions must be defined as named functions. Lambda expressions  (e.g., `x -> x > 0`) are not supported.
