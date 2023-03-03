# mathml2latex
一个小众的工具类，主要功能是将mathml转为latex公式。常用于教育行业，媒体行业。

Mathml各个节点参考https://developer.mozilla.org/zh-CN/docs/Web/MathML

设计思路：
将Mathml各个节点对应的功能，转化为latex语法。性能基本是毫秒级。

使用方法:
下载本类，调用mml2Latex方法，传入mathml数据。返回latex结构
里面有一些lombok类，apache commons的类，这些可根据使用者自行调整。
如有疑问可以联系我微sanjijiji

测试
String mml = "<?xml version=\"1.0\" encoding=\"UTF-16\"?>\n" +
            "<mml:math\n" +
            "    xmlns:mml=\"http://www.w3.org/1998/Math/MathML\"\n" +
            "    xmlns:m=\"http://schemas.openxmlformats.org/officeDocument/2006/math\">\n" +
            "    <mml:mi>f</mml:mi>\n" +
            "    <mml:mfenced separators=\"|\">\n" +
            "        <mml:mrow>\n" +
            "            <mml:mi>x</mml:mi>\n" +
            "        </mml:mrow>\n" +
            "    </mml:mfenced>\n" +
            "    <mml:mo>=</mml:mo>\n" +
            "    <mml:msub>\n" +
            "        <mml:mrow>\n" +
            "            <mml:mi>a</mml:mi>\n" +
            "        </mml:mrow>\n" +
            "        <mml:mrow>\n" +
            "            <mml:mn>0</mml:mn>\n" +
            "        </mml:mrow>\n" +
            "    </mml:msub>\n" +
            "    <mml:mo>+</mml:mo>\n" +
            "    <mml:mrow>\n" +
            "        <mml:msubsup>\n" +
            "            <mml:mo stretchy=\"true\">∑</mml:mo>\n" +
            "            <mml:mrow>\n" +
            "                <mml:mi>n</mml:mi>\n" +
            "                <mml:mo>=</mml:mo>\n" +
            "                <mml:mn>1</mml:mn>\n" +
            "            </mml:mrow>\n" +
            "            <mml:mrow>\n" +
            "                <mml:mi>∞</mml:mi>\n" +
            "            </mml:mrow>\n" +
            "        </mml:msubsup>\n" +
            "        <mml:mrow>\n" +
            "            <mml:mfenced separators=\"|\">\n" +
            "                <mml:mrow>\n" +
            "                    <mml:msub>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mi>a</mml:mi>\n" +
            "                        </mml:mrow>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mi>n</mml:mi>\n" +
            "                        </mml:mrow>\n" +
            "                    </mml:msub>\n" +
            "                    <mml:mrow>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mi mathvariant=\"normal\">cos</mml:mi>\n" +
            "                        </mml:mrow>\n" +
            "                        <mml:mo>\u2061</mml:mo>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mfrac>\n" +
            "                                <mml:mrow>\n" +
            "                                    <mml:mi>n</mml:mi>\n" +
            "                                    <mml:mi>π</mml:mi>\n" +
            "                                    <mml:mi>x</mml:mi>\n" +
            "                                </mml:mrow>\n" +
            "                                <mml:mrow>\n" +
            "                                    <mml:mi>L</mml:mi>\n" +
            "                                </mml:mrow>\n" +
            "                            </mml:mfrac>\n" +
            "                        </mml:mrow>\n" +
            "                    </mml:mrow>\n" +
            "                    <mml:mo>+</mml:mo>\n" +
            "                    <mml:msub>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mi>b</mml:mi>\n" +
            "                        </mml:mrow>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mi>n</mml:mi>\n" +
            "                        </mml:mrow>\n" +
            "                    </mml:msub>\n" +
            "                    <mml:mrow>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mi mathvariant=\"normal\">sin</mml:mi>\n" +
            "                        </mml:mrow>\n" +
            "                        <mml:mo>\u2061</mml:mo>\n" +
            "                        <mml:mrow>\n" +
            "                            <mml:mfrac>\n" +
            "                                <mml:mrow>\n" +
            "                                    <mml:mi>n</mml:mi>\n" +
            "                                    <mml:mi>π</mml:mi>\n" +
            "                                    <mml:mi>x</mml:mi>\n" +
            "                                </mml:mrow>\n" +
            "                                <mml:mrow>\n" +
            "                                    <mml:mi>L</mml:mi>\n" +
            "                                </mml:mrow>\n" +
            "                            </mml:mfrac>\n" +
            "                        </mml:mrow>\n" +
            "                    </mml:mrow>\n" +
            "                </mml:mrow>\n" +
            "            </mml:mfenced>\n" +
            "        </mml:mrow>\n" +
            "    </mml:mrow>\n" +
            "</mml:math>";

String latex = mml2Latex(mml);
System.out.println(latex);


输出结果
f \left (  x  \right ) = { a }_{ 0 } + { ∑ }_{ n  =  1 }^{ ∞ }\left ( { a }_{ n }\text{ cos } ⁡ \frac{ n  π  x }{ L } + { b }_{ n }\text{ sin } ⁡ \frac{ n  π  x }{ L } \right )
