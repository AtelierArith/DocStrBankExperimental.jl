```
dice_coeff_loss(ŷ, y; smooth = 1)
```

Return a loss based on the dice coefficient. Used in the [V-Net](https://arxiv.org/abs/1606.04797) image segmentation architecture. The dice coefficient is similar to the F1_score. Loss calculated as:

```
1 - 2*sum(|ŷ .* y| + smooth) / (sum(ŷ.^2) + sum(y.^2) + smooth)
```

# Example

```jldoctest
julia> y_pred = [1.1, 2.1, 3.1];

julia> Flux.dice_coeff_loss(y_pred, 1:3)
0.000992391663909964

julia> 1 - Flux.dice_coeff_loss(y_pred, 1:3)  # ~ F1 score for image segmentation
0.99900760833609
```
