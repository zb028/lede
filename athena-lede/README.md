# Athena RE-CS-02 LEDE build starter

This is a **validation-first** GitHub Actions workflow for a fork of `coolsnowwolf/lede`.
It has **not been tested on hardware** and **does not guarantee image compatibility** with your U-Boot partition layout.

1. Copy `.github/workflows/athena.yml` and `configs/athena-base.config` into your fork, retaining paths.
2. Commit to your default branch.
3. Actions -> Athena RE-CS-02 LEDE -> Run workflow. Leave `build=false` for the first run.
4. Inspect the logs and download `athena-config` artifact. If target/device validation fails, stop: do not flash anything.
5. After successful validation, rerun with `build=true`. Check the output manifest and image naming. Never flash without checking U-Boot type, CDT/GPT partition scheme, backup/recovery access and image format.

This starter intentionally excludes NSS, LED and proxy/Docker packages. Those require verification of kernel, device-specific driver and feed compatibility. It also does not explicitly select Wi-Fi packages: confirm board defaults and firmware blobs before flashing.

GitHub runner disk and time constraints may cause builds to fail even with correct configuration. A successful compile is not proof of bootability.
