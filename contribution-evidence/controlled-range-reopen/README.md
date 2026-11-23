# Controlled multi-month range reopening

Source commit: `3a4970db677ec4624c0253aabbf9a7f8981b6a7a`. Baseline: `548a1f3464c30741f2581c78f27fe1f20f9aeac6`.

Select February 10–15 in the second panel, close using the parent's `open` prop, and reopen. Before the fix the first panel is January; after the fix it is February. With an external April range update while closed, the first panel changes from March to April. The input value stays correct in both versions.

Native mouse interaction matrix: Chromium and Firefox, 1280px and 680px viewports, controlled and uncontrolled inputs, with and without an external range update. Eight controlled cases fail before; all sixteen cases pass after. Uncontrolled cases pass in both versions. WebKit and physical mobile devices were not tested. Screenshots are unmodified browser captures using the source stylesheet compiled with Sass to an explicit output file.

| Browser, viewport, external update | Before                                               | After                                              |
| ---------------------------------- | ---------------------------------------------------- | -------------------------------------------------- |
| chromium, 1280px, false            | [Before](chromium-1280-selected-february-before.png) | [After](chromium-1280-selected-february-after.png) |
| firefox, 1280px, false             | [Before](firefox-1280-selected-february-before.png)  | [After](firefox-1280-selected-february-after.png)  |
| chromium, 1280px, true             | [Before](chromium-1280-external-april-before.png)    | [After](chromium-1280-external-april-after.png)    |
| firefox, 1280px, true              | [Before](firefox-1280-external-april-before.png)     | [After](firefox-1280-external-april-after.png)     |
| chromium, 680px, true              | [Before](chromium-680-external-april-before.png)     | [After](chromium-680-external-april-after.png)     |
| firefox, 680px, true               | [Before](firefox-680-external-april-before.png)      | [After](firefox-680-external-april-after.png)      |
| chromium, 680px, false             | [Before](chromium-680-selected-february-before.png)  | [After](chromium-680-selected-february-after.png)  |
| firefox, 680px, false              | [Before](firefox-680-selected-february-before.png)   | [After](firefox-680-selected-february-after.png)   |

Three unit regressions fail on baseline; final full Jest coverage run passes 1,488 tests across 44 suites. Formatting, types, lint and JS build pass. The normal CSS build scripts returned empty redirected output in this runner; explicit Sass output-file compilation verified nonempty CSS assets for validation. One intermediate full-suite run failed an unchanged TimeComponent test; the final full run passes.

Prepared with AI assistance.
