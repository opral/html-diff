# Limitations

## ⚠️ `data-diff-key` Required

Diff quality depends on stable `data-diff-key` attributes being present in the rendered HTML.

Without these attributes, the HTML differ cannot reliably match elements between the "before" and "after" versions, which may result in:

- Poor diff quality
- Elements being marked as completely removed/added instead of modified
- Inability to track changes within nested structures

## Best Practices

- Ensure `data-diff-key` attributes are stable across renders
- Use semantic, unique identifiers derived from durable app or content identity
- Include `data-diff-key` on all elements you want to track changes for
- Avoid dynamically generated IDs that change between renders
- Avoid position-only fallback keys for ordered prose or markdown; deleting one paragraph can shift later positions and cause unrelated siblings to be matched

If you need to synthesize keys, prefer this fallback order:

1. Existing persisted IDs from your app or content model
2. Stable content or block IDs generated when the content is created
3. Matching unchanged siblings by text or signature
4. Render position only as a last resort
