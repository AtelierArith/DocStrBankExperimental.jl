Stabilizer, i.e. a list of commuting multi-qubit Hermitian Pauli operators.

Instances can be created with the `S` custom string macro or as direct sum of other stabilizers.

!!! tip "Stabilizers and Destabilizers"
    In many cases you probably would prefer to use the [`MixedDestabilizer`](@ref) data structure, as it caries a lot of useful additional information, like tracking rank and destabilizer operators. `Stabilizer` has mostly a pedagogical value, and it is also used for slightly faster simulation of a particular subset of Clifford operations.


```jldoctest stabilizer
julia> s = S"XXX
             ZZI
             IZZ"
+ XXX
+ ZZ_
+ _ZZ

julia> s⊗s
+ XXX___
+ ZZ____
+ _ZZ___
+ ___XXX
+ ___ZZ_
+ ____ZZ
```

It has an indexing API, looking like a list of `PauliOperator`s.

```jldoctest stabilizer
julia> s[2]
+ ZZ_
```

Pauli operators can act directly on the a stabilizer.

```jldoctest stabilizer
julia> P"YYY" * s
- XXX
+ ZZ_
+ _ZZ
```

There are a number of ways to create a Stabilizer, including:

  * generate Stabilizers from a list of Pauli operators

```jldoctest stabilizer
julia> Stabilizer([P"XX", P"ZZ"])
+ XX
+ ZZ
```

  * generate Stabilizers from boolean matrices

```jldoctest stabilizer
julia> a = [true true; false false]; b = [false true; true true];

julia> Stabilizer(a, b)
+ XY
+ ZZ

julia> Stabilizer([0x0, 0x2], a, b)
+ XY
- ZZ
```

  * initialize an empty Stabilizer and fill it through indexing

```jldoctest stabilizer
julia> s = zero(Stabilizer, 2)
+ __
+ __

julia> s[1,1] = (true, false); s
+ X_
+ __
```

There are no automatic checks for correctness (i.e. independence of all rows, commutativity of all rows, hermiticity of all rows). The rank (number of rows) is permitted to be less than the number of qubits (number of columns): canonilization, projection, etc. continue working in that case. To great extent this library uses the `Stabilizer` data structure simply as a tableau. This might be properly abstracted away in future versions.

See also: [`PauliOperator`](@ref), [`canonicalize!`](@ref)
