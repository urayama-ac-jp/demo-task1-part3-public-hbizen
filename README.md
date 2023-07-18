# 【Level1-1】ユーザー名の表示（静的）
## テーマ
1. ControllerおよびModelクラスの取り扱いについて  

## 演習課題の準備（開発環境について）
* この演習では、Codespacesと呼ばれるサービスを使って開発を行います。
* ブラウザ上で動作する開発環境です、インストール不要で使う事ができます。
* レベル0で実施した[手順](/Codespacesの実行手順.md)を参照して、演習課題の準備をしましょう。

## 演習内容
Portalページに表示されている、「こんにちは、○○さん」の表示を変更しましょう。  
「○○さん」の部分を自分の名前に変更して下さい。  

# ヒント・解説
## Controllerクラス
Portalページを表示するために、`PortalController`クラスが利用されます。  
このクラスには`@Controller`と`@RequestMapping("/")`というアノテーションがついています。  
`PortalController`クラスには`index`メソッドのみ存在します。  
このメソッドには、`@GetMapping()`アノテーションがついています。  

| アノテーション | 役割 | 
| --- | --- |
| @Controller | コントローラーである事を示すアノテーションです。 |
| @RequestMapping("/") | パスのないURLに対してリクエストがあった際に、このクラスでリクエストを処理する事を示します。|
|  @GetMapping() | GETリクエストを処理するメソッドである事を示します。 |

## Modelクラス
コントローラーからビュー側へデータを渡す時に使用されるクラスです。  
Modelクラスのオブジェクトに`model.addAttribute`メソッドを使用して値を設定しています。  
`model.addAttribute`メソッドの第一引数に属性名、第二引数に渡したい値を指定しています。  
```
model.addAttribute("name", "○○"); // ○○を書き換えて名前を表示  
```
今回は、属性名はそのままに、名前として渡している`○○`の値を自分の名前に変更すればOKです。  

## ビューの動きについて
indexメソッドは戻り値に`"index"`が指定されているため、`index.html`ファイルをテンプレートとして使用し、HTMLを生成します。  
modelオブジェクトで渡した、属性名`name`のデータについては以下の部分で使用されています。  
```
<span class="text-black fw-bold" th:text="${name}">名前</span>さん
```

今回使用している、Thymeleafというテンプレートエンジンでは、テンプレートファイルに、  
`th:text="${属性名}"`の形式で記載すると、コントローラーで設定した、値で、タグ内の値が置き換えられます。  

# 課題の提出
## GitHubへの提出
* 以下の操作を行い課題を提出しましょう。
1. Commit(コミット)
* Commitは、追加・変更したファイルをGitに登録するための操作です。

2. Push(プッシュ)
* pushは、コミットした内容をローカルレポジトリからリモートリポジトリに送信する操作です。

3. Pull Request(プルリクエスト)
* Pull Requestは、開発者のローカルレポジトリでの変更を他の開発者に通知する機能です。

### 手順
1. 木の枝のようなマークを押します。<br>
![image](https://user-images.githubusercontent.com/32722128/149911899-77da4cf0-cf8e-4b74-af63-1592156f4e9c.png)

2. これまでに行ったファイルへの変更ないようが表示されています。
* 変更内容に問題がないか今一度確認しましょう。 
![image](https://user-images.githubusercontent.com/32722128/149912420-00d3f65f-d50c-4b78-a0d6-1dfae21389f1.png)

3. コミットするファイルを選択しましょう。
* コミットしたいファイルの横の＋ボタンを押しましょう。
![image](https://user-images.githubusercontent.com/32722128/149912930-bd2d559c-0456-41d0-82bc-aa32376ad3c4.png)

4. Staged Changesにコミットしたいファイルが含まれていることを確認しましょう。<br>
![image](https://user-images.githubusercontent.com/32722128/149913113-2b2f3b32-ea97-41f6-b805-60dd5b05d2dc.png)

5. Message欄にCommit Message(コミットメッセージ)を入力しましょう。
* Commit Messageには、今回のコミットの追加・変更内容について記載します。
* 今回は「「○○さん」の部分を自分の名前に変更」としておきましょう。
![image](https://user-images.githubusercontent.com/32722128/149915153-848dd391-5a21-4581-a2f8-a1f635f97386.png)

6. チェックボタンを押してコミットしましょう。<br>
![image](https://user-images.githubusercontent.com/32722128/149915586-633c9a2f-06e4-4815-89f3-3008bfe4cfdc.png)

7. Sync Changesボタンを押してコミットをプッシュしましょう。<br>
![image](https://user-images.githubusercontent.com/32722128/149915829-c0834f7e-5db2-49cb-9047-94f2474c7d3f.png)

8. ダイアログが出ますので「OK」を押しましょう。<br>
![image](https://user-images.githubusercontent.com/32722128/149915978-5eeba149-394a-4bba-bcc2-c9afd620681d.png)

9. Sync Changesボタンが消えていることを確認してください。<br>
![image](https://user-images.githubusercontent.com/32722128/149916219-5940a267-d83e-4b1d-a3b5-6fb6a11c3a90.png)

10. 画面左下の緑のボタンを押しましょう。<br>
![image](https://user-images.githubusercontent.com/32722128/149916623-5677f1e5-a18a-4dda-a8f0-ff486ef98ec5.png)

11. 画面中央上部の「現在のCodespaceを中断する」を押します。
![image](https://user-images.githubusercontent.com/32722128/149916882-182b2b1c-8cd2-4317-a2b0-6a7f085811b9.png)

12. タブを×ボタンで閉じましょう。<br>
![image](https://user-images.githubusercontent.com/32722128/149917438-0d04f110-2f42-44b1-b599-7a020dd83993.png)

13. 画面コピーの画面に戻ります。<br>
![image](https://user-images.githubusercontent.com/32722128/149993006-9c23498e-f725-4199-a92d-a6d2d4a26347.png)

14. 「Pull requests」ボタンを押します。<br>
![image](https://user-images.githubusercontent.com/32722128/149993180-14ce060f-364e-473c-9250-aa13a7235f68.png)

15.　講師からのフィードバックがある場合は、この画面に表示されます。<br>
![image](https://user-images.githubusercontent.com/32722128/149993320-3cf0c0ce-c495-4e9d-8665-0f2978c457b4.png)

# 課題を提出したら、Codespacesを終了しましょう
* Codespacesはブラウザタブの×ボタンで閉じないようにしてください、以下の手順で終了してください。
1. 画面左下の緑のボタンを押しましょう。
![image](https://user-images.githubusercontent.com/32722128/149916623-5677f1e5-a18a-4dda-a8f0-ff486ef98ec5.png)

2. 画面中央上部の「現在のCodespaceを中断する」を押します。
![image](https://user-images.githubusercontent.com/32722128/149916882-182b2b1c-8cd2-4317-a2b0-6a7f085811b9.png)

3. タブを×ボタンで閉じましょう。
![image](https://user-images.githubusercontent.com/32722128/149917438-0d04f110-2f42-44b1-b599-7a020dd83993.png)

