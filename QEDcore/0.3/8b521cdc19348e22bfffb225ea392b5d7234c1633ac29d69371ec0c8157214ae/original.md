```
FlatPhaseSpaceLayout{INPSL} <: QEDbase.AbstractOutPhaseSpaceLayout{INPSL}
```

Defines a flat phase space layout for generating outgoing particle momenta. This layout assumes that outgoing particles are uniformly distributed in phase space, subject to constraints on momentum and energy conservation. This is accomplished by exploiting the RAMBO [Kleiss:1985gy](@cite) (Random Momenta Beautifully Organized) algorithm to generate the momenta, supporting both massless and massive particles.

# Fields

  * `in_psl::INPSL`: Input phase space layout, which provides the initial state layout for the process. This field links to the input configuration, making it accessible for consistency across related calculations.

# Usage

`FlatPhaseSpaceLayout` is commonly used in high-energy physics to define phase space configurations for event generators and cross-section calculations. Key functions include:

  * `QEDbase.phase_space_dimension`: Calculates the phase space dimension based on the number of outgoing particles.
  * `QEDbase._build_momenta`: Constructs the outgoing momenta using the provided phase space layout and RAMBO-based algorithms, ensuring the momenta satisfy energy and momentum conservation laws.

# Example

```julia
# Define input and process information, model, and input coordinates
psl = FlatPhaseSpaceLayout(input_psl)
build_momenta(process, model, incoming_momenta, psl, out_coords)
```

`FlatPhaseSpaceLayout` provides a robust setup for defining the final-state phase space in particle physics simulations, allowing for modularity and compatibility with `QEDbase` routines.
