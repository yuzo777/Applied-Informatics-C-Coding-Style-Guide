
命名規則
==========

命名規則
--------

規約事項 25
^^^^^^^^^^^

すべてのクラスライブラリは、一意となる名前空間を定義する必要があります。

規約事項 26
^^^^^^^^^^^

クラスライブラリ内に存在する、外部から使用可能なクラス、列挙型、型定義、関数、定数、
および変数の識別子は、クラスライブラリの名前空間内に定義されている必要があります。

規約事項 27
^^^^^^^^^^^

変数と関数の名前は、小文字で始める必要があります。

規約事項 28
^^^^^^^^^^^

抽象データ型、クラス、構造体、型、および列挙型の名前は、大文字で始める必要があります。

規約事項 29
^^^^^^^^^^^

2つ以上の単語で構成される名前では、単語は一緒に書き込まれ、最初の単語に続く単語は大文字で始まります。 [#f1]_ 

規約事項 30
^^^^^^^^^^^

グローバル名は1つまたは2つのアンダースコア（"_"または"__"）で始めてはなりません。
このような名前はコンパイラで使用するために予約されているため、C++標準では禁止されています。

.. _rule31:

規約事項 31
^^^^^^^^^^^

定数と列挙値の例外を除いて、名前にアンダースコアを使ってはいけません。（名前の最初の文字の後） [#f2]_ 

規約事項 32
^^^^^^^^^^^

大文字と小文字の区別だけが異なる型名は使用しないでください。

.. _rule33:

規約事項 33
^^^^^^^^^^^

privateおよびprotectedなメンバ変数の名前は、単一のアンダースコアで始まります。
アンダースコアで始まる名前の唯一のケースです。（:ref:`規約事項31<rule31>` を参照）

規約事項 34
^^^^^^^^^^^

定数の名前と列挙値はすべて大文字です。 2つ以上の単語で構成される名前では、これらの単語はアンダースコアで区切られています。

規約事項 35
^^^^^^^^^^^

クラス内のグローバル変数と定数、列挙型、およびtypedefをカプセル化します。

推奨事項 5
^^^^^^^^^^

名前はできるだけ簡潔に説明する必要があります。潜在的な省略名は、読みにくいものと長すぎるものです。

推奨事項 6
^^^^^^^^^^

名前は発音可能でなければなりません。発音できないことについて話し合うのは難しいです。

推奨事項 7
^^^^^^^^^^

名前には、一般に認められていない略語は含まれていてはなりません。一般的に受け入れられている略語のリストは、付録で見つけることができます。

.. _recommendation8:

推奨事項 8
^^^^^^^^^^

ポインタを保持する変数にはプレフィックス"p"を付ける必要があります。
参照を保持する変数にはプレフィックス"r"を付ける必要があります。
イテレータを保持する変数にはプレフィックス"it"を付ける必要があります。

推奨事項 9
^^^^^^^^^^

:ref:`推奨事項8<recommendation8>` のケースは除き、暗号のような名前は避ける必要があります。
暗号のような名前は、誰も読むことができません。特に、タイプエンコードされた変数名（lpcszNameのようなPetzold形式のハンガリー表記）は避けてください。

推奨事項 10
^^^^^^^^^^^^

名前には一貫性を持たせてください。一度使われた名前は、どこであっても同じ意味を持たなければなりません。
（例えば、idのような抽象的な名前は、プログラムによって別の意味を持つことがあります。これは適切ではありません。）

クラス宣言内の識別子の例を以下に示します。（コメントは削除されています）

.. code-block:: cpp
  :caption: 例3

  class Net_API HTTPRequest: public HTTPMessage
  {
  public:
      HTTPRequest();
      HTTPRequest(const std::string& version);
      HTTPRequest(const std::string& method, const std::string& uri);
      virtual ~HTTPRequest();
      void setMethod(const std::string& method);
      const std::string& getMethod() const;
      void write(std::ostream& ostr) const;
      void read(std::istream& istr);
      static const std::string HTTP_GET;
      static const std::string HTTP_HEAD;
      static const std::string HTTP_PUT;
      static const std::string HTTP_POST;
      static const std::string HTTP_OPTIONS;
      static const std::string HTTP_DELETE;
      static const std::string HTTP_TRACE;
      static const std::string HTTP_CONNECT;
  
  private:
      enum Limits
      {
          MAX_METHOD_LENGTH = 32,
          MAX_URI_LENGTH = 4096,
          MAX_VERSION_LENGTH = 8
      };
  
      std::string _method;
      std::string _uri;
  };


.. rubric:: 脚注

.. [#f1] キャメルケースとしてよく知られる記法です。
.. [#f2] privateおよびprotectedなメンバ変数の名前の先頭のアンダースコア（ :ref:`規約事項33<rule33>` を参照）はここではカウントされません。