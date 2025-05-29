```julia
get_example_network_params(name)

```

Makes named example neural networks available as a [`NeuralNet`](@ref) object.

# Arguments

  * `name::String`: Name of example neural network. Options:

      * `'MNIST.n1'`:

          * Architecture: Two fully connected layers with 40 and 20 units.
          * Training: Trained regularly with no attempt to increase robustness.
      * `'MNIST.WK17a_linf0.1_authors'`.

          * Architecture: Two convolutional layers (stride length 2) with 16 and 32 filters respectively (size 4 × 4 in both layers), followed by a fully-connected layer with 100 units.
          * Training: Network trained to be robust to attacks with $l_\infty$ norm at most 0.1 via method in [Provable defenses against adversarial examples via the convex outer adversarial polytope](https://arxiv.org/abs/1711.00851). Is MNIST network for which results are reported in that paper.
      * `'MNIST.RSL18a_linf0.1_authors'`.

          * Architecture: One fully connected layer with 500 units.
          * Training: Network trained to be robust to attacks with $l_\infty$ norm at most 0.1 via method in [Certified Defenses against Adversarial Examples ](https://arxiv.org/abs/1801.09344). Is MNIST network for which results are reported in that paper.
