```
hbnlsolve(w::NTuple{N,Number}, Nharmonics::NTuple{N,Int}, sources,
    circuit, circuitdefs; iterations = 1000,
    maxintermodorder = Inf, dc = false, odd = true, even = false,
    x0 = nothing, ftol = 1e-8, switchofflinesearchtol = 1e-5,
    alphamin = 1e-4, symfreqvar = nothing, sorting= :number)
```

Harmonic balance solver supporting an arbitrary number of large signals (strong tones or pumps) and arbitrary numbers of ports, sources, and drives including direct current (zero frequency) or flux pumping using a current source and a mutual inductor. Use `hblinsolve` to linearize the system of equations about the operating point found with `hbnlsolve`.

# Arguments

  * `w::NTuple{N,Number}`: a tuple containing the angular frequencies of the   strong tones (or pumps) such as (2*pi*5.0e9,) for a single tone at 5   GHz and (2*pi*5.0e9,2*pi*6.0e9) for a tone at 5 GHz and a tone at   6 GHz. The frequencies should be non-commensurate. For commensurate   frequencies, the lowest frequency should be provided here, and the other   added to `sources` with a mode index equal to the ratio.
  * `Nharmonics::NTuple{N,Int}`: a tuple of integers describing how many   harmonics to simulate for each of the tones. The length of the tuple must   equal the number of non-commensurate tones.
  * `sources::Vector`: a vector of named tuples specifying the mode index,   port, and current for each source. The named tuple(s) have names   mode, port, and current. mode is a tuple specifying the mode or harmonic   indices of the pumps, port is an integer specifying the port, and current   is a number specifying the current. Note that the current is a complex   number    For example:   [(mode=(1,0),port=1,current=Ip1),(mode=(0,1),port=1,current=Ip2)]   specifies two pumps where the frequency of the first pump would be   1*wp1 + 0*wp2 and the second 0*wp1+1*wp2 where wp1 is the first   pump frequency and wp2 is the second pump frequency. Both of the pumps are   applied to port 1 with currents Ip1 and Ip2, respectively.
  * `circuit`: vector of tuples each of which contain the component name, the   first node, the second node, and the component value. The first three must   be strings.
  * `circuitdefs`: a dictionary where the keys are symbols or symbolic   variables for component values and the values are the numerical values   for the components.

# Keywords

  * `iterations = 1000`: the number of iterations before the nonlinear solver   returns an error.
  * `maxintermodorder = Inf`: the maximum intermod order as defined by the sum of   the absolute values of the integers multiplying each of the frequencies   being less than or equal to `maxintermodorder`. This performs a diamond   truncation of the discrete Fourier space.
  * `dc = false`: include 0 frequency terms in the harmonic balance analysis.
  * `odd = true`: include odd terms in the harmonic balance analysis.
  * `even = false`: include even terms in the harmonic balance analysis.
  * `x0 = nothing`: initial value for the nodeflux.
  * `ftol = 1e-8`: the function tolerance defined we considered converged,   defined as norm(F)/norm(x) < ftol or norm(F,Inf) <= ftol.
  * `switchofflinesearchtol = 1e-5`:
  * `alphamin = 1e-4`: the function tolerance at which we switch   from Newton with linesearch to only Newton. For easily converging   functions, setting this to zero can speed up simulations.
  * `symfreqvar = nothing`: the symbolic frequency variable, eg `w`.
  * `sorting = :number`: sort the nodes by:   `:name`: Sort the vector of strings. This always works but leads   to results like "101" comes before "11".   `:number`: Convert the node strings to integer and sort by these   (this errors if the nodes names cannot be converted to integers).   `:none`: Don't perform any sorting except to place the ground node   first. In other words, order the nodes in the order they are found in   `circuit`.

# Returns

  * `NonlinearHB`: A simple structure to hold the harmonic balance solutions.   See [`NonlinearHB`](@ref).

# Examples

```jldoctest
circuit = Tuple{String,String,String,Union{Complex{Float64},Symbol,Int64}}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("L1","1","0",:Lm)) 
push!(circuit,("K1","L1","L2",:K1))
push!(circuit,("C1","1","2",:Cc)) 
push!(circuit,("L2","2","3",:Lm)) 
push!(circuit,("Lj3","3","0",:Lj)) 
push!(circuit,("Lj4","2","0",:Lj)) 
push!(circuit,("C2","2","0",:Cj))
circuitdefs = Dict{Symbol,Complex{Float64}}(
    :Lj =>2000e-12,
    :Lm =>10e-12,
    :Cc => 200.0e-15,
    :Cj => 900e-15,
    :Rleft => 50.0,
    :Rright => 50.0,
    :K1 => 0.9,
)

Idc = 50e-5
Ip=0.0001e-6
wp=2*pi*5e9
Npumpmodes = 2
out=hbnlsolve(
    (wp,),
    (Npumpmodes,),
    [
        (mode=(0,),port=1,current=Idc),
        (mode=(1,),port=1,current=Ip),
    ],
    circuit,circuitdefs;dc=true,odd=true,even=false)
isapprox(out.nodeflux[:],
    ComplexF64[15.190314040027522 - 8.56492651167657e-24im, 2.991103820177504e-6 - 1.8501001011477133e-8im, -6.835392148510984 - 1.0356102442254259e-14im, 7.396422335315908e-6 - 4.5749403967992827e-8im, 6.835392148539885 - 1.0356102451770844e-14im, 1.008026285172782e-5 - 6.23498762664213e-8im],
    atol = 1e-6)

# output
true
```
