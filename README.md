# River flood simulator (floodsim) and window app — companion source for the book

Design documents and code for the river flood simulator built in ***Toward a Million Lines XIII — Building a River Flood Simulator*** (Japanese title 『LLM で 100 万行のソフトウェア開発 XIII — 河川氾濫のシミュレータをつくる』; the book is in Japanese).

`floodsim` (Python) computes the water that spreads over a low-lying city when a levee breaks, and the rain water that a sewer cannot take. It solves the shallow-water equations with a **one-dimensional river channel**, a **two-dimensional floodplain** (a finite-volume HLL scheme and a fast local-inertial scheme) and a **one-dimensional sewer pipe network with pumps**, joined by exchanges of water level and discharge, with levee breach and overtopping, lake sluice gates and pumping stations, and nested grids. It runs an **idealized levee breach**, an **idealized urban sewer flood**, an **idealized lake basin** and a synthetic-terrain pipeline (no data needed), and **real-terrain cases** from the elevation data of the Geospatial Information Authority of Japan (a breach of the Arakawa levee, the 1947 Kathleen typhoon, pluvial flooding, pluvial plus fluvial flooding with pump shutdown, and the Inba-numa basin), and writes animations and figures (maximum depth, arrival time, duration, maximum speed, mass balance). A Windows **window app** (Flutter) sets the parameters, starts the computation, shows progress and plays the animations. **The window holds no computation of its own**: every button runs a `floodsim` command and reads the result files it writes. In this project **the design documents are the source of the code**.

## Download

**The ready-to-run app and the source are on the [Releases](../../releases) page**, not in this repository. The release has four separate ZIPs:

| File | Contents |
|:---|:---|
| `floodsim_exe.zip` | The Windows window app, ready built (**Japanese screens**), with the simulator it runs, the case-file templates and a small-example launcher |
| `floodsim_exe_en.zip` | The same app (**English screens** by default) |
| `floodsim.zip` | Design documents (`docs/`, Japanese, L1-L4, the source; `docs_en/`, the complete set for English readers: L1-L3 translated into English, L4 the Japanese originals as is) in separate folders, the code (`src/floodsim/`, `app/`), the requirements specification (57 requirements), the case-file templates, and empty databases (`ledger/`) |
| `floodsim_animations.zip` | The animations of the calculations of the book (cases A–E and the Inba-numa 2026 typhoon No. 25 runs): 2-D animations as MP4 video files only |

The app needs Python 3.11 and numpy, scipy, numba, matplotlib, pillow, pyproj and psutil on your PC (see the README inside the ZIPs); extract to a short path. Start the app with the launcher (`floodsim_ja.cmd` / `floodsim_en.cmd`), which tells it where the simulator is. There is **no APK** (the app is a Windows desktop app). The app is **not code-signed**, so Windows may warn you. Computation results and tests are not included. The elevation data is not included; the window can fetch the GSI elevation tiles for you. The first run takes a few minutes (numba compiles); try the bundled small example first. The calculations are results of a model, not forecasts, and must not be used as hazard maps.

You are free to change the design documents and the code and compare the results.

---

## License

- **The author holds the copyright.**
- **The code is under the GNU General Public License v3.0 or later (GPL-3.0-or-later).** The full text is [`LICENSE`](LICENSE). **If you modify it and distribute it, you must publish the source under the same GPL-3.0-or-later terms.**
- **The design documents and the text are under the Creative Commons Attribution-ShareAlike 4.0 International license (CC BY-SA 4.0).** This covers `docs/`, `docs_en/`, the READMEs and the other written text of this repository, and the text of the matching book. See [`LICENSE-DOCS.md`](LICENSE-DOCS.md).
- **If you use them, say so.** State where it came from (the title of the book and the name of this repository) and keep the copyright notice. If you changed it, say that you changed it.
- **In this project the design documents are the source of the code.** When you publish something made from this code, **publish the design documents together with the code.**
- Third-party components (numpy, scipy, numba, matplotlib, pillow, pyproj, psutil installed by `pip install .`; the Flutter engine inside the EXEs) remain under their own original licenses.
- Provided "as is", without warranty — as the GPL-3.0 text says.

## 著作権とライセンス

- **著作権は、著者にあります。**
- **コードは、GNU General Public License v3.0 以降（GPL-3.0-or-later）です。**全文は [`LICENSE`](LICENSE) です。**改変して配布するときは、同じ GPL-3.0 以降の条件で、ソースを公開する義務があります。**
- **設計書と文章は、Creative Commons 表示-継承 4.0 国際（CC BY-SA 4.0）です。**このリポジトリの `docs/`・`docs_en/`・README ほかの文章と、対応する本の文章が当たります。内容は [`LICENSE-DOCS.md`](LICENSE-DOCS.md) です。
- **使ったときは、使ったことを書いてください。**どこから使ったか（本の題名と、このリポジトリの名前）と、著作権の表示を、使った先に書いてください。直したときは、直したことも書いてください。
- **このプロジェクトでは、設計書がコードの源です。**コードを使って作ったものを公開するときは、**設計書も、コードと一緒に公開してください。**
- 第三者の部品（`pip install .` で入る numpy・scipy・numba・matplotlib・pillow・pyproj・psutil、EXE の中の Flutter の engine）は、それぞれの元のライセンスのままです。
- 現状のまま（as is）提供します。保証はありません（GPL-3.0 の全文のとおりです）。
