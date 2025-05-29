Represents a tropical Puiseux polynomial, i.e. a tropical polynomial in several variables, whose  exponents might be rational numbers (i.e. we use this structure when T is a subtype of the rational numbers). The coefficients are elements of the tropical semiring.

# Example

julia> f = TropicalPuiseuxPoly(Dict([1, 2] => 1, [2, 1] => 2), [[1, 2], [2, 1]])   TropicalPuiseuxPoly{Int64}(Dict([2, 1] => 2, [1, 2] => 1), [[1, 2], [2, 1]])
