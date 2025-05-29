High-level wrapper for VkPhysicalDeviceVulkan13Properties.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkan13Properties.html)

```julia
struct PhysicalDeviceVulkan13Properties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `min_subgroup_size::UInt32`
  * `max_subgroup_size::UInt32`
  * `max_compute_workgroup_subgroups::UInt32`
  * `required_subgroup_size_stages::Vulkan.ShaderStageFlag`
  * `max_inline_uniform_block_size::UInt32`
  * `max_per_stage_descriptor_inline_uniform_blocks::UInt32`
  * `max_per_stage_descriptor_update_after_bind_inline_uniform_blocks::UInt32`
  * `max_descriptor_set_inline_uniform_blocks::UInt32`
  * `max_descriptor_set_update_after_bind_inline_uniform_blocks::UInt32`
  * `max_inline_uniform_total_size::UInt32`
  * `integer_dot_product_8_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_8_bit_signed_accelerated::Bool`
  * `integer_dot_product_8_bit_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_8_bit_packed_unsigned_accelerated::Bool`
  * `integer_dot_product_8_bit_packed_signed_accelerated::Bool`
  * `integer_dot_product_8_bit_packed_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_16_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_16_bit_signed_accelerated::Bool`
  * `integer_dot_product_16_bit_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_32_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_32_bit_signed_accelerated::Bool`
  * `integer_dot_product_32_bit_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_64_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_64_bit_signed_accelerated::Bool`
  * `integer_dot_product_64_bit_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_8_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_8_bit_signed_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_8_bit_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_8_bit_packed_unsigned_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_8_bit_packed_signed_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_8_bit_packed_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_16_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_16_bit_signed_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_16_bit_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_32_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_32_bit_signed_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_32_bit_mixed_signedness_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_64_bit_unsigned_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_64_bit_signed_accelerated::Bool`
  * `integer_dot_product_accumulating_saturating_64_bit_mixed_signedness_accelerated::Bool`
  * `storage_texel_buffer_offset_alignment_bytes::UInt64`
  * `storage_texel_buffer_offset_single_texel_alignment::Bool`
  * `uniform_texel_buffer_offset_alignment_bytes::UInt64`
  * `uniform_texel_buffer_offset_single_texel_alignment::Bool`
  * `max_buffer_size::UInt64`
