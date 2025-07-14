# change-detection




┌──────────────────────────────┐
│  Browser (Next.js 15 app)    │
│ ─ Upload “before / after”    │
│ ─ pixelmatch runs client-side │
│ ─ Renders diff-mask canvas    │
│ ─ Calls /api/mcp ability      │
└──────────────┬───────────────┘
               │  JSON {ability:"captionGPT", …}
               ▼
┌────────────────────────────────────────────┐
│  /api/mcp  (Vercel Edge Function)          │
│  @vercel/mcp-adapter                       │
│  ─ ability: captionGPT                    │
│       ↳ GPT-4o Vision API                 │
│  ─ (hook for more abilities later)         │
└────────────────────────────────────────────┘
               │  {caption:"A new pier…"}
               ▼
┌──────────────────────────────┐
│  UI shows caption toast +    │
│  diff mask overlay           │
└──────────────────────────────┘
