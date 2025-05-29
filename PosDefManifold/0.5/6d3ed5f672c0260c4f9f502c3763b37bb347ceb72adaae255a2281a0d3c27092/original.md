```
    (1) ispos(λ::Vector{T};
	<
	tol::Real=0,
	rev=true,
	🔔=true,
	msg="">)

    (2) ispos(Λ::𝔻{T};
	< same optional keyword arguments as in (1) > )

	for all above: where T<:Real
```

Return $true$ if all numbers in (1) real vector $λ$ or in (2) real `Diagonal`  matrix $Λ$ are not inferior to $tol$, otherwise return $false$. This is used,  for example, in spectral functions to check that all eigenvalues are positive.

!!! note "Nota Bene"
    $tol$ defaults to the square root of `Base.eps` of the type of $λ$ (1)  or $Λ$ (2). This corresponds to requiring positivity beyond about half of  the significant digits.


The following are *<optional keyword arguments>*:

  * If $rev=true$ the (1) elements in $λ$ or (2) the diagonal elements

in $Λ$ will be chacked in reverse order.  This is done for allowing a very fast check when the elements  are sorted and it is known from where is best to start checking.

If the result is $false$:

  * if $🔔=true$ a bell character will be printed. In most systems this will ring a bell on the computer.
  * if string $msg$ is provided, a warning will print $msg$ followed by:

"at position *pos*", where *pos* is the position where the  first non-positive element has been found.

**Examples**

```julia
using PosDefManifold
a=[1, 0, 2, 8]
ispos(a, msg="non-positive element found")

# it will print:
# ┌ Warning: non-positive element found at position 2
# └ @ [here julie will point to the line of code issuing the warning]
```
