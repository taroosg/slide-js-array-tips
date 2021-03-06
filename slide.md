---
transition: "slide"
title: "配列を制すものはJavaScriptを制す"
---

配列を制すものは JavaScript を制す

<div style="display:flex;justify-content:space-evenly;background:lightgray;">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/800px-Unofficial_JavaScript_logo_2.svg.png" alt="" style="height:150px;">
<!-- <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Deno.svg/1200px-Deno.svg.png" alt="" style="height:150px;">
<img src="https://is3-ssl.mzstatic.com/image/thumb/Purple126/v4/05/bb/5a/05bb5ab0-7505-3a7b-f29e-78ddb6f20dbc/AppIcon-85-220-0-4-2x.png/1200x630bb.png" alt="" style="height:150px;"> -->
</div>

---

::: block
自己紹介 {style=background:#3e62ad;width:1000px}
:::

--

|         |                                      |
| ------- | ------------------------------------ |
| Name    | 大杉太郎（たろさん，たろ先生）       |
| Age     | 34 （1987 年生まれ）                 |
| Place   | 茨城県 -> 北海道 -> 東京都 -> 福岡県 |
| Career  | ジーズアカデミー福岡主任講師         |
| Like1   | Rust，Node.js，本，旅行，断捨離      |
| Like2   | 🥃, 🍺, 🍷                           |
| twitter | @taro_osg                            |

---

もくじ

- 配列使ってますか？？
- JS で配列を扱うときのコツ
- `map()` や `filter()` の小技
- `new Array()` 使ってる？？
- `...` の威力
- 分割代入
- まとめなど

---

配列使ってますか？？

--

JS のさしすせそ

```js
["最初は", "仕上げは", "全ては", "世界は", "そう，"]
  .map((x) => `${x}配列`)
  .join("\n");

// 最初は配列
// 仕上げは配列
// 全ては配列
// 世界は配列
// そう，配列
```

--

JS で配列あまり使えてない人は多い．．！

--

`"配列" > ("繰り返し" || "条件分岐") `

`// true`

---

JS で配列を扱うときのコツ

--

1. 配列の中身は触るな．．！

--

JS の配列は「参照」である！

--

```js
const array01 = [2, 3, 5, 7, 11, 13, 17, 19, 23, 27, 29];
const array02 = array1;

// array1 に 31 を追加
array01.push(31);

console.log(array01);
console.log(array02);
```

--

結果

```js
// array01
[2, 3, 5, 7, 11, 13, 17, 19, 23, 27, 29, 31];

// array02
[2, 3, 5, 7, 11, 13, 17, 19, 23, 27, 29, 31];
```

--

元の配列を変更するとヤバい．．！

--

2. 「インデックス」をうまく使え！

--

```js
// あたりはずれのどちらかを出したい
const data = ["あたり", "はずれ"];

// 条件分岐より配列だッ！
data[~~(Math.random() * 2)];
```

--

コツ

- 元の配列は弄らない．
- 処理を加えた「別の配列」をつくる．
- インデックスをうまく使う．

---

`map()` や `filter()` の小技

--

配列に一定の処理を加えた「新しい配列」を生成

--

基本

```js
[1, 2, 3, 4, 5, 6, 7, 8, 9].map((x) => x * 2);

// [2, 4, 6, 8, 10, 12, 14, 16, 18]
```

--

第 2 引数に index を取れる

```js
// 初項2，公差3の等差数列をつくる

[0, 0, 0, 0, 0, 0, 0, 0, 0].map((x, i) => x + 2 + i * 3);
```

--

第 3 引数に元の配列を取れる

```js
// 例：時系列のデータ
const data01 = [2, 3, 5, 7, 11, 13, 17, 20, 23, 27, 29, 31];

// 最終項の値に対する%に換算したい
data01.map((x, i, arr) => (x / arr.slice(-1)[0]) * 100);
```

---

`new Array()` 使ってる？？

--

けっこう便利な場面もある．

```js
// 長さ100で全部0が入った配列を作りたい
new Array(100).fill(0);
```

---

`...` の威力

--

（時々みるけどググれないやつ）

--

（スプレッド構文）

--

```js
// 例：2つの配列をマージしたい
const array01 = [2, 3, 5];
const array02 = [7, 11, 13];

// array01とarray02には影響しない
const array03 = [...array01, ...array02];
```

---

分割代入

--

最大値最小値の例

```js
// 例：順番が適当なデータ
const data04 = [20, 5, 13, 29, 3, 11, 2, 27, 7, 17, 31, 23];

// 最大値と最小値を取得したい
// 結果には`[2, 31]`の配列が入る
const [min, max] = data04
  .sort((a, b) => a - b)
  .filter((x, i, arr) => i === 0 || i === arr.length - 1);
```

---

まとめなど

--

データは配列形式のことが多い．

--

配列は慣れないとバグを生みやすい．

--

配列の処理を自分で書けるようになると

世界が広がる

--

配列と仲良くなろう！！
